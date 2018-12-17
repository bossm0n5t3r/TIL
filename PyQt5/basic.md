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
          self.setWindowTitle('My First Application')
          self.move(300, 300)
          self.resize(400, 200)
          self.show()


  if __name__ == '__main__':

      APP = QApplication(sys.argv)
      ex = MyApp()
      sys.exit(APP.exec_())

```

  - ["pylint can't find QWidget and QApplication" 에러가 발생한 경우](https://stackoverflow.com/questions/46337716/pylint-cant-find-qwidget-and-qapplication)
    - 같은 폴더에 다음 코드를 .pylintrc 파일을 생성해서 입력 후 저장

```
  [MASTER]
  extension-pkg-whitelist=PyQt5
```

  - [pylint 가 "missing module docstring" 라는 오류를 나타낸 경우](http://meonggae.blogspot.com/2017/03/git-pylint-pep8.html)