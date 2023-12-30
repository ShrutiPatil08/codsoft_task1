from tkinter import *
from tkinter import messagebox

win=Tk()
win.geometry('600x600+400+150')
win.title('Task 1')
l1=Label(win,text='To Do List',font='times_new_roman 22 bold',bg='orange',bd=5)
l1.pack(side='top',fill=BOTH)

l1=Label(win,text='Enter Task',font='calibri 18 bold',bg='orange')
l1.place(x=10,y=70)
entry=Entry(win, font='calibri 18')
entry.place(x=150,y=70)


def add_task():
    task = entry.get()
    if task:
        task_listbox.insert(END, task)
        entry.delete(0,END)
    else:
        messagebox.showwarning("Empty Task", "Please enter a task.")

def remove_task():
    selected_index = task_listbox.curselection()
    if selected_index:
        task_listbox.delete(selected_index)
    elif task_listbox.size() > 0:
        task_listbox.delete(END)
    else:
        messagebox.showinfo("Empty List", "The task list is already empty.")

def delete_all_tasks():
    if task_listbox.size() > 0:
        task_listbox.delete(0, END)
        messagebox.showinfo("All Tasks Deleted", "All tasks have been deleted.")
    else:
        messagebox.showinfo("Empty List", "The task list is already empty.")

def exit_program():
    if messagebox.askokcancel("Exit", "Do you really want to exit?"):
        win.destroy()

btn=Button(win,text='Add',font='calibri 15 bold',width=12,bd=4,bg='orange',command=add_task)
btn.place(x=10,y=130)
btn=Button(win,text='Remove ',font='calibri 15 bold',width=12,bd=4,bg='orange',command=remove_task)
btn.place(x=210,y=130)
btn=Button(win,text='Delete All',font='calibri 15 bold',width=12,bd=4,bg='orange',command=delete_all_tasks)
btn.place(x=400,y=130)
btn=Button(win,text='Exit',font='calibri 15 bold',width=55,bd=4,bg='orange',command=exit_program)
btn.place(x=10,y=520)

task_listbox = Listbox(win, width=47, height=10,font='calibri 18')
task_listbox.place(x=10,y=200)

win.mainloop()
