# MemoryCard

# main



from PyQt5.QtWidgets import QWidget , QApplication

app = QApplication([])
from layout_quizz import *
window = QWidget()
window.resize(600 , 500)
window.setWindowTitle("Memory Card")
window.setLayout(main_line_quizz)
menu_window = QWidget()
menu_window.resize(600 , 500)
menu_window.setWindowTitle("Memory Card")
menu_window.setLayout(main_line_menu)
window.show()

def click():
    if btn.text() == "Відповісти":
        box.hide()
        box2.show()
        btn.setText("Наступне питання")
    else:
        box2.hide()
        box.show()
        btn.setText("Відповісти")

def click_menu():
    menu_window.show()
    window.hide()

def click_menu_exit():
    window.show()
    menu_window.hide()

def exit():
    app.exit()    

btn.clicked.connect(click)
btn_menu.clicked.connect(click_menu)
btn_menu_quit.clicked.connect(click_menu_exit)
btn_menu2.clicked.connect(exit)

app.exec()



#layout_quizz



from PyQt5.QtWidgets import (QPushButton , QRadioButton , QLabel , QSpinBox , QGroupBox ,
                             QButtonGroup , QHBoxLayout , QVBoxLayout)
from PyQt5.QtCore import Qt

btn_menu = QPushButton("Меню")
btn_rest = QPushButton("Відпочити")

spin = QSpinBox()
spin.setValue(30)

box = QGroupBox()
box2 = QGroupBox()
Group = QButtonGroup()

label = QLabel("______")
btn1 = QRadioButton("___")
btn2 = QRadioButton("___")
btn3 = QRadioButton("___")
btn4 = QRadioButton("___")
btn = QPushButton("Відповісти")
btn_menu_quit = QPushButton("Почати тестування")
btn_menu1 = QPushButton("Почати заучування")
btn_menu2 = QPushButton("Вийти")

ans_text = QLabel("Правильно")
ans_text2 = QLabel("apple")

Group.addButton(btn1)
Group.addButton(btn2)
Group.addButton(btn3)
Group.addButton(btn4)


main_line_quizz = QVBoxLayout()
main_line_menu = QVBoxLayout()
line_box = QHBoxLayout()
line_box2 = QHBoxLayout()
line1_quizz = QHBoxLayout()
line2_quizz = QVBoxLayout()
line3_quizz = QVBoxLayout()
line1_quizz.addWidget(btn_menu)
line1_quizz.addStretch(1)
line1_quizz.addWidget(btn_rest)
line1_quizz.addWidget(spin)
line1_quizz.addWidget(QLabel("хвилин"))
line2_quizz.addWidget(btn1)
line2_quizz.addWidget(btn2)
line3_quizz.addWidget(btn3)
line3_quizz.addWidget(btn4)
main_line_quizz.addLayout(line1_quizz)
main_line_quizz.addWidget(label)
main_line_quizz.addWidget(box, stretch=5)
line_box.addLayout(line2_quizz)
line_box.addLayout(line3_quizz)
box.setLayout(line_box)
box2.setLayout(line_box2)

line_box2.addWidget(ans_text , alignment = Qt.AlignTop)
line_box2.addWidget(ans_text2)

main_line_quizz.addWidget(box2, stretch=5)

box2.hide()
main_line_quizz.addWidget(btn , alignment = Qt.AlignCenter)
main_line_menu.addWidget(btn_menu_quit , alignment = Qt.AlignCenter)
main_line_menu.addWidget(btn_menu1 , alignment = Qt.AlignCenter)
main_line_menu.addWidget(btn_menu2 , alignment = Qt.AlignCenter)
