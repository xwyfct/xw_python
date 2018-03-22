# xw_python
#Data analysis by python
#Cylinder_milage.py
# coding=gbk

from tkFileDialog1 import Getfile
e = Getfile()
load_f=e.getfile()
f1=open(load_f)
fre_line = f1.readlines()
fre = fre_line[1].split('\t')

from Load_dis import *
loadfile_list = get_file()
milage_list = []
for loadfile in loadfile_list:
	pitch_angle_list = loadfile_to_angle(loadfile)
	milage = angle_to_milage(pitch_angle_list)
	milage_list.append(milage)

milage_a_list = []
for j in range(0,len(fre)-1):
	milage_a = float(fre[j])*milage_list[j]
	milage_a_list.append(milage_a)
Totalmilage_a = sum(milage_a_list)


fmpath = e.selectTMilespath()+r'\TMiles.txt'
f2 = open(fmpath,'a')
for milage_a in milage_a_list:
	f2.write(str(milage_a)+'\n')
f2.write('annual milages'+'\t')
f2.write(str(Totalmilage_a)+'\n')
f2.close()

