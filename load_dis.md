# xw_python
#Data analysis by python
#load_dis.py
# coding=gbk
import os,math
from tkFileDialog1 import Getfile
def angle_to_milage(pitch_angle_list):
	cylinder_position_list = []
	angle_init = 60.975
	R_b = 1.75
	R_d = 0.625
	for angle in pitch_angle_list:
		L = (R_b**2+R_d**2-2*R_b*R_d*math.cos((angle+angle_init)*(math.pi)/180))**0.5
		cylinder_position_list.append(L)
	milage = 0
	for i in range(0,len(cylinder_position_list)-1):
		L_gap = abs(cylinder_position_list[i+1]-cylinder_position_list[i])
		milage += L_gap
	return milage
def loadfile_to_angle(loadfile):
	f = open(loadfile)
	lines = f.readlines()
	pitch_angle_list = []
	for raw in lines[3:]:
		raw = raw.split('\t')
		angle = float(raw[3])
		pitch_angle_list.append(angle)
	return pitch_angle_list
def get_file():
	e = Getfile()
	file_path = e.getfilepath()
	loadfile_list = []
	for root,dirs,files in os.walk(file_path):
	    for fn in files:
		    loadfile = str('%s//%s'%(root,fn))
		    loadfile_list.append(loadfile)
	return loadfile_list
