## LESSON 6: GRAPHICAL UIs (GUIs)

## WINDOWS

Windows are a graphical representation of a program, and can contain things like buttons, input boxes, images, etc. -- pretty much anything you want, with the proper import/library/dependency.

For example, when you open up a program like Chrome or Steam or Discord, the program opens a *window*. In order to create these windows and the user interfaces contained inside, you can import some *APIs* like **Tkinter** (older and simpler) or **PyQt5**/**PyQt6** (newer, more updated, and sleeker).

Here is a complete script that opens a simple, small window using PyQt6, with basic functionality like a *menu bar* at the top, minimize/maximize/close buttons in the top corner, and some text.

example:
```
import sys
from PyQt6.QtWidgets import QApplication, QMainWindow, QLabel, QMessageBox
from PyQt6.QtGui import QAction
from PyQt6.QtCore import Qt

class MainWindow(QMainWindow):
    def __init__(self):
        super().__init__()
        self.setWindowTitle("Example Window w/ PyQt6")
        self.resize(420, 220)

        # Central text
        label = QLabel(
            "Lorem ipsum dolor sit amet, consectetur adipiscing elit, "
            "sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."
        )
        label.setWordWrap(True)
        label.setAlignment(Qt.AlignmentFlag.AlignLeft | Qt.AlignmentFlag.AlignTop)
        label.setMargin(12)
        self.setCentralWidget(label)

        # Menu bar
        menubar = self.menuBar()

        file_menu = menubar.addMenu("&File")
        exit_action = QAction("E&xit", self)
        exit_action.triggered.connect(self.close)
        file_menu.addAction(exit_action)

        help_menu = menubar.addMenu("&Help")
        about_action = QAction("&About", self)
        about_action.triggered.connect(self.show_about)
        help_menu.addAction(about_action)

    def show_about(self):
        QMessageBox.about(self, "About this program", "A tiny PyQt6 demo window showing some text.")

def main():
    app = QApplication(sys.argv)
    window = MainWindow()
    window.show()
    sys.exit(app.exec())

if __name__ == "__main__":
    main()
```


## USER INTERFACES (UIs)

*TBD*

example:
```
import sys
from PyQt6.QtWidgets import (
    QApplication, QMainWindow, QWidget, QLabel, QMessageBox,
    QVBoxLayout, QHBoxLayout, QLineEdit, QTextEdit, QPushButton,
    QCheckBox
)
from PyQt6.QtGui import QAction


class MainWindow(QMainWindow):
    def __init__(self):
        super().__init__()
        self.setWindowTitle("Lorem Ipsum Viewer")
        self.resize(560, 420)

        self._build_ui()
        self._build_menu()
        self.statusBar().showMessage("Ready", 2000)

    def _build_ui(self):
        central = QWidget(self)
        self.setCentralWidget(central)

        vbox = QVBoxLayout(central)
        vbox.setContentsMargins(10, 10, 10, 10)
        vbox.setSpacing(10)

        # Title / info text
        title = QLabel(
            "Lorem ipsum dolor sit amet, consectetur adipiscing elit, "
            "sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."
        )
        title.setWordWrap(True)
        vbox.addWidget(title)

        # Input row
        in_row = QHBoxLayout()
        self.input = QLineEdit()
        self.input.setPlaceholderText("Type something and press Add or Enter...")
        self.input.returnPressed.connect(self.add_text)

        btn_add = QPushButton("Add")
        btn_add.clicked.connect(self.add_text)

        btn_clear = QPushButton("Clear")
        btn_clear.clicked.connect(self.clear_text)

        btn_copy = QPushButton("Copy")
        btn_copy.clicked.connect(self.copy_text)

        in_row.addWidget(self.input, 1)
        in_row.addWidget(btn_add)
        in_row.addWidget(btn_clear)
        in_row.addWidget(btn_copy)
        vbox.addLayout(in_row)

        # Text area
        self.text = QTextEdit()
        self.text.setAcceptRichText(False)
        self.text.setPlainText(
            "Lorem ipsum dolor sit amet, consectetur adipiscing elit.\n"
            "Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.\n"
            "Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris."
        )
        vbox.addWidget(self.text, 1)

        # Options row
        opt_row = QHBoxLayout()
        self.wrap_check = QCheckBox("Wrap text")
        self.wrap_check.setChecked(True)
        self.wrap_check.toggled.connect(self.toggle_wrap)

        opt_row.addWidget(self.wrap_check)
        opt_row.addStretch(1)
        vbox.addLayout(opt_row)

    def _build_menu(self):
        menubar = self.menuBar()

        file_menu = menubar.addMenu("&File")
        exit_action = QAction("E&xit", self)
        exit_action.setShortcut("Ctrl+Q")
        exit_action.triggered.connect(self.close)
        file_menu.addAction(exit_action)

        edit_menu = menubar.addMenu("&Edit")
        copy_action = QAction("&Copy", self)
        copy_action.setShortcut("Ctrl+C")
        copy_action.triggered.connect(self.copy_text)
        clear_action = QAction("C&lear", self)
        clear_action.setShortcut("Ctrl+L")
        clear_action.triggered.connect(self.clear_text)
        edit_menu.addAction(copy_action)
        edit_menu.addAction(clear_action)

        help_menu = menubar.addMenu("&Help")
        about_action = QAction("&About", self)
        about_action.setShortcut("F1")
        about_action.triggered.connect(self.show_about)
        help_menu.addAction(about_action)

    # Actions
    def add_text(self):
        text = self.input.text().strip()
        if not text:
            QMessageBox.information(self, "Nothing to add", "Please type something first.")
            return
        self.text.append(text)
        self.input.clear()
        self.input.setFocus()
        self.statusBar().showMessage("Text added", 1500)

    def clear_text(self):
        self.text.clear()
        self.input.clear()
        self.input.setFocus()
        self.statusBar().showMessage("Cleared", 1500)

    def copy_text(self):
        cursor = self.text.textCursor()
        if cursor.hasSelection():
            to_copy = cursor.selectedText()
        else:
            to_copy = self.text.toPlainText()
        if to_copy:
            QApplication.clipboard().setText(to_copy)
            self.statusBar().showMessage("Copied to clipboard", 1500)
        else:
            self.statusBar().showMessage("Nothing to copy", 1500)

    def toggle_wrap(self, checked: bool):
        mode = QTextEdit.LineWrapMode.WidgetWidth if checked else QTextEdit.LineWrapMode.NoWrap
        self.text.setLineWrapMode(mode)

    def show_about(self):
        QMessageBox.about(
            self,
            "About Lorem Ipsum Viewer",
            "A tiny PyQt6 demo with text, inputs, buttons, menus."
        )


def main():
    app = QApplication(sys.argv)
    window = MainWindow()
    window.show()
    sys.exit(app.exec())


if __name__ == "__main__":
    main()
```


## GRAPHICS & DESIGN

*TBD*

example:
```
import sys
from PyQt6.QtWidgets import (
    QApplication, QMainWindow, QWidget, QLabel, QMessageBox,
    QVBoxLayout, QHBoxLayout, QLineEdit, QTextEdit, QPushButton,
    QCheckBox, QSpinBox
)
from PyQt6.QtGui import QAction
from PyQt6.QtCore import Qt


class MainWindow(QMainWindow):
    def __init__(self):
        super().__init__()
        self.setWindowTitle("Lorem Ipsum Viewer")
        self.resize(560, 420)

        # Simple styling
        self.setStyleSheet("""
            QMainWindow { background: #f6f7fb; }
            QLabel#title { font-size: 16px; font-weight: 600; padding: 6px; color: #333; }
            QTextEdit, QLineEdit { background: #ffffff; border: 1px solid #c8c8c8; border-radius: 6px; padding: 6px; }
            QPushButton { background: #2d89ef; color: white; border: none; border-radius: 6px; padding: 6px 10px; }
            QPushButton:hover { background: #1e70d0; }
            QPushButton:disabled { background: #9bb9e7; }
        """)

        self._build_ui()
        self._build_menu()
        self.statusBar().showMessage("Ready", 2000)

    def _build_ui(self):
        central = QWidget(self)
        self.setCentralWidget(central)

        vbox = QVBoxLayout(central)
        vbox.setContentsMargins(10, 10, 10, 10)
        vbox.setSpacing(10)

        # Title / info text
        title = QLabel(
            "Lorem ipsum dolor sit amet, consectetur adipiscing elit, "
            "sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."
        )
        title.setObjectName("title")
        title.setWordWrap(True)
        vbox.addWidget(title)

        # Input row
        in_row = QHBoxLayout()
        self.input = QLineEdit()
        self.input.setPlaceholderText("Type something and press Add or Enter...")
        self.input.returnPressed.connect(self.add_text)

        btn_add = QPushButton("Add")
        btn_add.clicked.connect(self.add_text)

        btn_clear = QPushButton("Clear")
        btn_clear.clicked.connect(self.clear_text)

        btn_copy = QPushButton("Copy")
        btn_copy.clicked.connect(self.copy_text)

        in_row.addWidget(self.input, 1)
        in_row.addWidget(btn_add)
        in_row.addWidget(btn_clear)
        in_row.addWidget(btn_copy)
        vbox.addLayout(in_row)

        # Text area
        self.text = QTextEdit()
        self.text.setAcceptRichText(False)
        base_font = self.text.font()
        base_font.setPointSize(12)
        self.text.setFont(base_font)
        self.text.setPlainText(
            "Lorem ipsum dolor sit amet, consectetur adipiscing elit.\n"
            "Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.\n"
            "Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris."
        )
        vbox.addWidget(self.text, 1)

        # Options row
        opt_row = QHBoxLayout()
        self.wrap_check = QCheckBox("Wrap text")
        self.wrap_check.setChecked(True)
        self.wrap_check.toggled.connect(self.toggle_wrap)

        size_label = QLabel("Font size:")
        self.size_spin = QSpinBox()
        self.size_spin.setRange(8, 24)
        self.size_spin.setValue(12)
        self.size_spin.valueChanged.connect(self.set_font_size)

        opt_row.addWidget(self.wrap_check)
        opt_row.addStretch(1)
        opt_row.addWidget(size_label)
        opt_row.addWidget(self.size_spin)
        vbox.addLayout(opt_row)

    def _build_menu(self):
        menubar = self.menuBar()

        file_menu = menubar.addMenu("&File")
        exit_action = QAction("E&xit", self)
        exit_action.setShortcut("Ctrl+Q")
        exit_action.triggered.connect(self.close)
        file_menu.addAction(exit_action)

        edit_menu = menubar.addMenu("&Edit")
        copy_action = QAction("&Copy", self)
        copy_action.setShortcut("Ctrl+C")
        copy_action.triggered.connect(self.copy_text)
        clear_action = QAction("C&lear", self)
        clear_action.setShortcut("Ctrl+L")
        clear_action.triggered.connect(self.clear_text)
        edit_menu.addAction(copy_action)
        edit_menu.addAction(clear_action)

        help_menu = menubar.addMenu("&Help")
        about_action = QAction("&About", self)
        about_action.setShortcut("F1")
        about_action.triggered.connect(self.show_about)
        help_menu.addAction(about_action)

    # Actions
    def add_text(self):
        text = self.input.text().strip()
        if not text:
            QMessageBox.information(self, "Nothing to add", "Please type something first.")
            return
        self.text.append(text)
        self.input.clear()
        self.input.setFocus()
        self.statusBar().showMessage("Text added", 1500)

    def clear_text(self):
        self.text.clear()
        self.input.clear()
        self.input.setFocus()
        self.statusBar().showMessage("Cleared", 1500)

    def copy_text(self):
        cursor = self.text.textCursor()
        if cursor.hasSelection():
            to_copy = cursor.selectedText()
        else:
            to_copy = self.text.toPlainText()
        if to_copy:
            QApplication.clipboard().setText(to_copy)
            self.statusBar().showMessage("Copied to clipboard", 1500)
        else:
            self.statusBar().showMessage("Nothing to copy", 1500)

    def toggle_wrap(self, checked: bool):
        mode = QTextEdit.LineWrapMode.WidgetWidth if checked else QTextEdit.LineWrapMode.NoWrap
        self.text.setLineWrapMode(mode)

    def set_font_size(self, size: int):
        font = self.text.font()
        font.setPointSize(size)
        self.text.setFont(font)

    def show_about(self):
        QMessageBox.about(
            self,
            "About Lorem Ipsum Viewer",
            "A tiny PyQt6 demo with text, inputs, buttons, menus, and simple styling."
        )


def main():
    app = QApplication(sys.argv)
    window = MainWindow()
    window.show()
    sys.exit(app.exec())


if __name__ == "__main__":
    main()
```