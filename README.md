import sys
import subprocess
from PyQt6.QtWidgets import QApplication, QWidget, QVBoxLayout, QPushButton, QLabel

class Launcher(QWidget):
    def __init__(self):
        super().__init__()

        self.setWindowTitle("Android Game Launcher")
        self.setGeometry(200, 200, 400, 300)

        layout = QVBoxLayout()

        self.title = QLabel("🎮 Android Game Launcher")
        layout.addWidget(self.title)

        self.start_btn = QPushButton("تشغيل Waydroid")
        self.start_btn.clicked.connect(self.start_waydroid)
        layout.addWidget(self.start_btn)

        self.stop_btn = QPushButton("إيقاف Waydroid")
        self.stop_btn.clicked.connect(self.stop_waydroid)
        layout.addWidget(self.stop_btn)

        self.setLayout(layout)

    def start_waydroid(self):
        subprocess.run(["waydroid", "session", "start"])

    def stop_waydroid(self):
        subprocess.run(["waydroid", "session", "stop"])


app = QApplication(sys.argv)
window = Launcher()
window.show()
sys.exit(app.exec())# Android-Battles
