# Weather-App
In this repository I had made a basic weather forecast app by using Python. I had used python libraries and API keys to check the current weather of the particular place..


from tkinter import *
from tkinter import ttk
import requests

def data_get():
    city = city_name.get()
    data = requests.get("https://api.openweathermap.org/data/2.5/weather?q="+city+"&appid=e48e04967a6bad59057f3546fc0c5050").json()
    w_label1.config(text = data["weather"][0]["main"])
    wb_label1.config(text = data["weather"][0]["description"])
    temp_label1.config(text= str(int(data["main"]["temp"]-273.15)))
    per_label1.config(text = data["main"]["pressure"])


win = Tk()
win.title("Weather Forecast App")
win.config(bg= "lightblue")
win.geometry("500x580")

name_label = Label(win,text="Weather Forecast App", 
                   font=("Time New Roman",30,"bold"))
name_label.place(x=25, y=50, height=50, width=450)

list_name = ["Andhra Pradesh","Arunachal Pradesh ","Assam","Bihar","Chhattisgarh","Goa","Gujarat","Haryana","Himachal Pradesh","Jammu and Kashmir","Jharkhand","Karnataka","Kerala","Madhya Pradesh","Maharashtra","Manipur","Meghalaya","Mizoram","Nagaland","Odisha","Punjab","Rajasthan","Sikkim","Tamil Nadu","Telangana","Tripura","Uttar Pradesh","Uttarakhand","West Bengal","Andaman and Nicobar Islands","Chandigarh","Dadra and Nagar Haveli","Daman and Diu","Lakshadweep","National Capital Territory of Delhi","Puducherry"]

city_name = StringVar()
com = ttk.Combobox(win, text="Weather Forecast App", values = list_name,
                   font=("Tine New Roman",20), textvariable= city_name)
com.place(x=25,y=120,height=50,width=450)



w_label = Label(win,text="Weather climate", 
                   font=("Time New Roman",20))
w_label.place(x=25, y=260, height=50, width=210)

w_label1 = Label(win,text="", 
                   font=("Time New Roman",20))
w_label1.place(x=250, y=260, height=50, width=210)

wb_label = Label(win,text="Weather Description", 
                   font=("Time New Roman",17))
wb_label.place(x=25, y=330, height=50, width=210)

wb_label1 = Label(win,text="", 
                   font=("Time New Roman",20))
wb_label1.place(x=250, y=330, height=50, width=210)

temp_label = Label(win,text="Temperature", 
                   font=("Time New Roman",20))
temp_label.place(x=25, y=400, height=50, width=210)

temp_label1 = Label(win,text="", 
                   font=("Time New Roman",20))
temp_label1.place(x=250, y=400, height=50, width=210)

per_label = Label(win,text="Pressure", 
                   font=("Time New Roman",20))
per_label.place(x=25, y=470, height=50, width=210)

per_label1 = Label(win,text="", 
                   font=("Time New Roman",20))
per_label1.place(x=250, y=470, height=50, width=210)

done_button = Button(win, text= "Done", 
                     font=("Time New Roman",20), command= data_get)
done_button.place(x=200,y=190,height=50,width=100)


win.mainloop()

