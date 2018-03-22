# xw_python
Data analysis by python

#!/usr/bin/env python
# coding=gbk
from tkinter import *
from tkinter.filedialog import *
class Getfile():
	
	def selectPath(self,path):
	    path_ = askdirectory()
	    path.set(path_)
	
	def selectFile(self,File):
		file_=askopenfilename(filetypes=(("Text files","*.txt"),("All files","*.*")))	
		File.set(file_)
		
	def getfilepath(self):  
		root = Tk()
		path = StringVar()
		root.title("load file path")
		root.geometry("600x300") 
		Label(root,text = "fatigue load file path:",font=("Arial",12)).grid(row = 0, column = 0)
		Entry(root, textvariable = path).grid(row = 0, column = 1)
		Button(root, text = "pathselect", command = self.selectPath(path)).grid(row = 0, column = 2)
		root.mainloop()
		file_path = path.get()
		return file_path
		
	def getfile(self):  
		root = Tk()
		File = StringVar()
		root.title("select load_f")
		root.geometry("600x300") 
		Label(root,text = "fatigue load_f:",font=("Arial",12)).grid(row = 0, column = 0)
		Entry(root, textvariable = File).grid(row = 0, column = 1)
		Button(root, text = "path select", command = self.selectFile(File)).grid(row = 0, column = 2)
		root.mainloop()
		filename = File.get()
		return filename
		
	def selectTMilespath(self):  
		root = Tk()
		path = StringVar()
		root.title("select storage path of total milage file")
		root.geometry("600x300") 
		Label(root,text = "path of total milage file:",font=("Arial",12)).grid(row = 0, column = 0)
		Entry(root, textvariable = path).grid(row = 0, column = 1)
		Button(root, text = "select path", command = self.selectPath(path)).grid(row = 0, column = 2)
		root.mainloop()
		file_path = path.get()
		return file_path
		
	def selectMdispath(self):  
		root = Tk()
		path = StringVar()
		root.title("select storage path of milage distribute")
		root.geometry("600x300") 
		Label(root,text = "storage path of milage distribute:",font=("Arial",12)).grid(row = 0, column = 0)
		Entry(root, textvariable = path).grid(row = 0, column = 1)
		Button(root, text = "select path", command = self.selectPath(path)).grid(row = 0, column = 2)
		root.mainloop()
		file_path = path.get()
		return file_path
