# Contact-App

from tkinter import *
import tkinter as tk
from tkinter import messagebox
from tkinter import simpledialog
import os


root = Tk()
root.title("Contact App")
print('welcome to contact app')
print('this stores contacts for customers')

contacts=[{"name":"pooja","number":1234566543,"email":"poojabhosale18@gmail.com"},
          {"name":"abc","number":87654323245,"email":"wertyui@gmail.com"},
          {"name":"lmn","number":468765432,"email":"nbvcxdf@gmail.com"}]

def show_contacts():
  d=[]
  for i in contacts:
    d.append(i['name'])
  messagebox.showinfo(title='Show contact', message=f"{','.join(d)}")


def add_contact():
  new_contact={}
  s=Entry_1.get()
  p=Entry_2.get()
  l=Entry_3.get()
  new_contact['name']=s
  new_contact['number']=p
  new_contact['email']=l
  contacts.append(new_contact)
  Entry_1.delete(0,len(Entry_1.get()))
  Entry_2.delete(0,len(Entry_2.get()))
  Entry_3.delete(0,len(Entry_3.get()))
  messagebox.showinfo(title='Update contact', message=f"NEW contact named {new_contact['name']} added")
    

def delete_contact():
  name = Entry_1.get()
  for i in contacts:
    if i['name'] == name:
      contacts.remove(i)
      break
  Entry_1.delete(0,len(Entry_1.get()))
  messagebox.showinfo(title='Contact deleted !!!!', message=f"contact successfully deleted")

def update_contact():
        name=Entry_1.get() 
        s=simpledialog.askstring(title='Enter name',prompt='Enter name to update')
        p=simpledialog.askstring(title='Enter number',prompt='Enter number to update')
        l=simpledialog.askstring(title='Enter email',prompt='Enter email to update')
        print(s,p,l)
        for i in contacts:
            if i["name"]==name:
              temp=i.copy()
              i['name']=s
              i['number']=p
              i['email']=l
        Entry_1.delete(0,len(Entry_1.get()))
        Entry_2.delete(0,len(Entry_2.get()))
        Entry_3.delete(0,len(Entry_3.get()))  
        messagebox.showinfo(title='Contact updated', message=f"{temp['name']},{temp['number']}{temp['email']} was updated to {i['name']},{i['number']},{i['email']}")


def Exit():
  root.destroy()
  return

Label_0= Label(root,text="Contact app",fg="black",font=("Times new roman", 30, 'bold'))
Label_0.grid(columnspan=6)
               
Label_1=Label(root,text="ENTER NAME",bg="#e8c1c7",fg="black",bd=8,font=("Times new roman", 12, 'bold'),width=25)
Label_1.grid(row=1,column=0)

Entry_1=Entry(root, font=("Times new roman", 14),bd=8,width=25)
Entry_1.grid(row=1,column=1)
 
Label_2=Label(root, text="ENTER NUMBER",height="1",bg="#e8c1c7",bd=8,fg="black", font=("Times new roman", 12, 'bold'),width=25)
Label_2.grid(row=2,column=0)

Entry_2= Entry(root, font=("Times new roman", 14),bd=8,width=25)
Entry_2.grid(row=2,column=1)
 
Label_3=Label(root, text="ENTER EMAIL",bg="#e8c1c7",bd=8,fg="black", font=("Times new roman", 12, 'bold'),width=25)
Label_3.grid(row=3,column=0)

Entry_3= Entry(root, font=("Times new roman", 14),bd=8,width=25)
Entry_3.grid(row=3,column=1)
               
Button_1= Button(root,text="ADD CONTACT",bd=8, bg="#49D810", fg="black", width=25, font=("Times new roman", 12),command=add_contact)
Button_1.grid(row=1,column=2, padx=10, pady=10)

var = tk.IntVar()
Button_2= Button(root, text="UPDATE ITEM",bd=8, bg="#49D810", fg="black", width =25, font=("Times new roman", 12),command=update_contact)
Button_2.grid(row=2,column=2, padx=40, pady=10)

Button_3= Button(root, text="DELETE STOCK",bd=8, bg="#49D810", fg="black", width =25, font=("Times new roman", 12),command=delete_contact)
Button_3.grid(row=3,column=2, padx=40, pady=10)

Button_4= Button(root, text="SHOW CONTACT",bd=8, bg="#49D810", fg="black", width =25, font=("Times new roman", 12),command=show_contacts)
Button_4.grid(row=6,column=1, padx=40, pady=10)


Button_6= Button(root,highlightcolor="blue",activebackground="red", text="Exit",bd=8, bg="#FF0000", fg="#EEEEF1", width=25, font=("Times", 18),command=Exit)
Button_6.grid(row=6,column=2, padx=40, pady=10)


 
root.mainloop()
