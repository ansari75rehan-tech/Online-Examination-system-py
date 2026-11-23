from tkinter import *

su = Tk()
su.title("Online Examination System")
su.geometry("600x500")
su.config(bg="lightblue")


questions = [
    "1. Which language is used for Python programming?",
    "2. Which keyword is used to define a function?",
    "3. Which function displays output?",
    "4. Which symbol is used for comments?",
    "5. Which data type stores True or False?"
]

options = [
    ["Python", "Java", "C++", "HTML"],
    ["function", "def", "define", "fun"],
    ["input()", "print()", "show()", "display()"],
    ["//", "#", "/*", "<!--"],
    ["int", "str", "bool", "float"]
]

answers = ["Python", "def", "print()", "#", "bool"]

i = 0
score = 0


L1 = Label(su, text="Student Name",
           font=("arial", 16), bg="lightblue")
L1.grid(row=0, column=0, pady=10)

E1 = Entry(su, font=("arial", 16))
E1.grid(row=0, column=1)


Q1 = Label(su, text="", font=("arial", 16),
           bg="lightblue")
Q1.grid(row=1, column=0, columnspan=2, pady=20)


v = StringVar()

R1 = Radiobutton(su, text="", variable=v,
                 value="", font=("arial", 14),
                 bg="lightblue")
R1.grid(row=2, column=0, sticky="w")

R2 = Radiobutton(su, text="", variable=v,
                 value="", font=("arial", 14),
                 bg="lightblue")
R2.grid(row=3, column=0, sticky="w")

R3 = Radiobutton(su, text="", variable=v,
                 value="", font=("arial", 14),
                 bg="lightblue")
R3.grid(row=4, column=0, sticky="w")

R4 = Radiobutton(su, text="", variable=v,
                 value="", font=("arial", 14),
                 bg="lightblue")
R4.grid(row=5, column=0, sticky="w")



def show_question():

    Q1.config(text=questions[i])

    R1.config(text=options[i][0], value=options[i][0])
    R2.config(text=options[i][1], value=options[i][1])
    R3.config(text=options[i][2], value=options[i][2])
    R4.config(text=options[i][3], value=options[i][3])

    v.set("")



def next_question():

    global i, score

    if v.get() == "":
        return

    if v.get() == answers[i]:
        score = score + 1

    i = i + 1

    if i < 5:

        show_question()

    else:

        Q1.config(text="Examination Completed!")

        R1.config(text="")
        R2.config(text="")
        R3.config(text="")
        R4.config(text="")

        B1.config(state=DISABLED)

        L2.config(
            text="Student: " + E1.get() +
            "\nYour Score: " + str(score) + "/5"
        )



B1 = Button(su, text="Next Question",
            font=("arial", 15),
            bg="yellow", fg="red",
            command=next_question)

B1.grid(row=6, column=0, pady=20)


L2 = Label(su, text="", font=("arial", 16),
           bg="lightblue")

L2.grid(row=7, column=0, columnspan=2)




show_question()



while True:

    try:
        su.update()

    except TclError:
        break
