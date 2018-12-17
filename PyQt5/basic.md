# 기본

## 0. 설치

  - [PyQt5 설치안내](http://pyqt.sourceforge.net/Docs/PyQt5/installation.html)

```
    pip3 install PyQt5
```

  - VSCode 를 사용할 시에 python의 경우 pylint 를 별도로 설치해야 한다.
  - [pylint 설치 안내](https://www.pylint.org/#install)

```
    pip install pylint
```
  - VSCode 에서 python 작성해야 하는 경우
    - 본인 컴퓨터에 [python을 설치](https://www.python.org/downloads/)
    - VSCode에서 Python 이라는 Extension을 설치 ([Python - Microsoft](https://marketplace.visualstudio.com/items?itemName=ms-python.python) - 참고용 웹)

## 1. 창 띄우기

  - 기본 코드 ([출처](https://wikidocs.net/21920))

```python
  '''
  import module
  '''

  import sys
  from PyQt5.QtWidgets import QApplication, QWidget

  class MyApp(QWidget):
      '''
      MyApp Class
      '''
      def __init__(self):
          super().__init__()
          self.init_ui()

      def init_ui(self):
          '''
          Set initial ui
          '''
          self.setWindowTitle('My First Application')   # 타이틀바에 나타나는 창의 제목
          self.move(300, 300)                           # 위젯을 스크린의 x = 300px, y = 300px의 위치로 이동
          self.resize(400, 200)                         # 위젯의 너비와 높이를 결정
          self.show()                                   # 위젯을 스크린에 보여줌


  if __name__ == '__main__':

      APP = QApplication(sys.argv)                      # 모든 PyQt5 어플리케이션은 어플리케이션 객체를 생성해야 한다.
      ex = MyApp()
      sys.exit(APP.exec_())

```
  - [QApplication 공식 문서](https://doc.qt.io/qt-5/qapplication.html)
  - ERROR
    - [pylint 가 "missing module docstring" 라는 오류를 나타낸 경우](http://meonggae.blogspot.com/2017/03/git-pylint-pep8.html)
    - ["pylint can't find QWidget and QApplication" 에러가 발생한 경우](https://stackoverflow.com/questions/46337716/pylint-cant-find-qwidget-and-qapplication)
      - 같은 폴더에 다음 코드를 .pylintrc 파일을 생성해서 입력 후 저장

```
  [MASTER]
  extension-pkg-whitelist=PyQt5
```
