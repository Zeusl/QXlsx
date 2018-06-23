# QXlsx

> *Read this in other languages: [English](README.md), :kr: [한국어](README.ko.md)*

<p align="center"> 
<img src="markdown.data/QXlsx2.jpg">
</p>

* QXlsx is excel file(*.xlsx) reader/writer library.
  * Because QtXlsx is no longer supported(2014), I created a new project that is based on QtXlsx. (2017-)
  * Development language of QXlsx is C++. (with Qt 5.x)
  * You don't need to use static library or dynamic shared object using QXlsx.

[![Built-with-Qt5-Badge](https://img.shields.io/badge/Built%20with-Qt5-green.svg)](https://www.qt.io/) [![Built-with-cpp-Badge](https://img.shields.io/badge/Built%20with-C%2B%2B-green.svg)](https://isocpp.org/) [![Xlsx-Badge](https://img.shields.io/badge/Library-xlsx-blue.svg)](https://www.ecma-international.org/publications/standards/Ecma-376.htm)

## Sample (Hello excel)

### :one: Writing excel file(*.xlsx)
```cpp
QXlsx::Document xlsx;
xlsx.write("A1", "Hello Qt!"); // write "Hello Qt!" to cell(A,1). it's shared string.
xlsx.saveAs("Test.xlsx"); // save the document as 'Test.xlsx'
```

### :two: Reading excel file(*.xlsx)
```cpp
Document xlsx("Test.xlsx"); // load excel file
if (!xlsx.isLoadPackage()) { 
	return; // failed to load excel
}
int row = 1; int col = 2;
Cell* cell = xlsx.cellAt(row, col); // get cell pointer. (row is 1. column is 2.)
if ( cell == NULL )
	continue; // cell vaule is not set
QVariant var = cell->readValue(); // read cell value (number(double), QDateTime, QString ...)
qDebug() << var; // display value
```

## How to set up
* See [How to setup QXlsx project](HowToSetProject.md)

## Test environment

| Qt        | Tool               | OS             | Build   |
| --------- | ----------------   | -------------- | ------- |
| Qt 5.10.1 | MingW              | Windows 32bit  | :smile: |
| Qt 5.9.2  | MingW              | Windows 32bit  | :smile: |
| Qt 5.9.1  | Visual Studio 2017 | Windows 64bit  | :smile: |
| Qt 5.9.1  | Visual Studio 2017 | Windows 32bit  | :smile: |
| Qt 5.9.1  | MingW              | Windows 32bit  | :smile: |
| Qt 5.9.1  | gcc+make           | Ubuntu 16/x64  | :smile: |
| Qt 5.6.0  | MingW              | Windows 32bit  | :smile: |
| Qt 5.5.1  | MingW              | Windows 32bit  | :smile: |
| Qt 5.5.0  | gcc+make           | Ubuntu 17/i686 | :smile: |
| Qt 5.2.0  | gcc+make           | Ubuntu 14/x64  | :smile: |
| Qt 5.0.1  | MingW              | Windows 32bit  | :smile: |

## To Test
- The following tests should be performed.
	- Microsoft Excel
	- Google Spreadsheet
	- LibreOffice Calc Spreasheet

![](markdown.data/LibreOffice-Google-XLSX.png)

- Unicode test ( :cloud: filename, :cloud: filepath, :sunny: data value)

## To Upgrade
- Develop the encryption function of xlsx
- Build and test on Android

## License and links
* ![](https://img.shields.io/badge/license-MIT-blue.svg) MIT License [https://opensource.org/licenses/MIT](https://opensource.org/licenses/MIT)
* ![](https://img.shields.io/badge/license-MIT-blue.svg) QtXlsx License (See Debao Zhang (2014) site) [https://github.com/dbzhang800/QtXlsxWriter](https://github.com/dbzhang800/QtXlsxWriter)
* Qt License (See Qt Company site) [https://www.qt.io/](https://www.qt.io/) 

## Contact
* Hi! I'm j2doll (aka Jay Two). My name is Korean and it is difficult for foreigners to pronounce it. Call me j2doll.
* Leave me a issue. [https://github.com/j2doll/QXlsx/issues](https://github.com/j2doll/QXlsx/issues)
	- If you are interested in participating in the project, please contact us by issue.
	- My native language is not English and my English is not fluent. Please, use EASY English. :-)
	
## Similar projects I'm going on
* Qxlnt [https://github.com/j2doll/Qxlnt](https://github.com/j2doll/Qxlnt)
	- Qxlnt is a helper project that allows xlnt to be used in Qt.
	- xlnt is a excellent library for usinf xlsx Excel files.
	- I was looking for a way to make it easy to use in Qt. Of course, cmake is compatible with Qt, but it is not convenient to use. So I created Qxlnt.
