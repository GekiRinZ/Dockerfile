# Build .exe

1. Cài đặt pyinstaller
`pip install pyinstaller`

2. Build file .py
`pyinstaller E:\BackupD\Python\PythonWeek1\ex2.py`

```sh
578 INFO: PyInstaller: 3.3.1
579 INFO: Python: 3.6.5
579 INFO: Platform: Windows-10-10.0.17134-SP0
584 INFO: wrote C:\Users\Administrator\ex2.spec
586 INFO: UPX is not available.
692 INFO: Extending PYTHONPATH with paths
['E:\\BackupD\\Python\\PythonWeek1', 'C:\\Users\\Administrator']
692 INFO: checking Analysis
741 INFO: checking PYZ
776 INFO: checking PKG
781 INFO: Bootloader c:\python 3.6\lib\site-packages\PyInstaller\bootloader\Windows-32bit\run.exe
782 INFO: checking EXE
795 INFO: checking COLLECT
8979 INFO: Building COLLECT out00-COLLECT.toc
8990 INFO: Appending archive to EXE C:\Users\Administrator\build\ex2\ex2.exe
9784 INFO: Building COLLECT out00-COLLECT.toc completed successfully.
```
File exe sẽ đc xuất tới `C:\Users\Administrator\build\ex2\ex2.exe`
