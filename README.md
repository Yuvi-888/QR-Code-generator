from tkinter import *
import pyqrcode
import tkinter
from pyqrcode import  create

def get_data():
        global data
        data=entry_url.get()
        if data=='':
            return None
        else:
            data=pyqrcode.create(data)
            img=data.xbm(scale=5)
            global qr_img
            qr_img=tkinter.BitmapImage(data=img,foreground='Black',background='yellow')
            label2.config(image=qr_img)
            label3.config(text=f'QR Code Successfully Generated.',font='lucida 14 bold')

root=Tk()
root.geometry('550x650')
root.minsize(width=550,height=650)
root.maxsize(width=550,height=650)
root.title('QR Code Generator')
root.iconbitmap("C:\\Users\\Yuvraj\\Downloads\\qrcode.ico")

label1=Label(root,text="QR Code Generator",font=('robotto',23,'bold'))
label1.pack(pady=12,fill=BOTH)

label4=Label(root,text='Enter URL',font='robotto 12 bold')
label4.pack()

entry_url=Entry(root,font='robotto 14',border=2)
entry_url.pack(pady=10)

generate_button=Button(root,text='Generate',font='robotto 14',command=get_data,relief=RAISED,bg='orange',border=3)
generate_button.pack(pady=8)

label2=Label(root)
label2.pack(pady=40)

label3=Label(root)
label3.pack()

root.mainloop()

