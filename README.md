# Client Side Excel Export using JavaScript

## Introduction

Various server-side binaries and support libraries are present to help us export grids / tables / data to excel sheets, but the same export handling at client side is a tough nut to crack. This plugin helps you achieve that, thereby providing advance features as well.

## Installation

* npm i @tarunbatta/excelexportjs

## Setup Dev Instance

* npm install -g grunt-cli

## Run on Dev Instance

* change module from "commonjs" to "es2015" in tsconfig.json
* live-server

## Build Dist

* grunt

## Create Git Tag

* git tag
* git tag -a 4.0.x -m "version 4.0.x"
* git push origin 4.0.x

## NPM Login

* npm login

## Publish Library

* npm publish

## Sample Usage

Import the library as follows,

```js
var excelExportJs = require("./excelExportJs");
```

or

```js
import { excelExportJs } from './excelExportJs';
```

The following is an example implementation where two tables are exported to an excel sheet,

```js
var cols = new Array<excelExportJs.eeColumn>();
cols.push(new excelExportJs.eeColumn('sNo', 'S.No.', new excelExportJs.eeColumnType(excelExportJs.eeCellTypes.Number), 25));
cols.push(new excelExportJs.eeColumn('name', 'Name', new excelExportJs.eeColumnType(excelExportJs.eeCellTypes.Html), 100));
cols.push(new excelExportJs.eeColumn('age', 'Age', new excelExportJs.eeColumnType(excelExportJs.eeCellTypes.Number), 25));
cols.push(new excelExportJs.eeColumn('dob', 'Date Of Birth', new excelExportJs.eeColumnType(excelExportJs.eeCellTypes.DateTime), 75));
cols.push(new excelExportJs.eeColumn('salary', 'Salary $', new excelExportJs.eeColumnType(excelExportJs.eeCellTypes.Float)));
cols.push(new excelExportJs.eeColumn('isActive', 'Is Active', new excelExportJs.eeColumnType(excelExportJs.eeCellTypes.Boolean)));
cols.push(new excelExportJs.eeColumn('marks', 'Marks %', new excelExportJs.eeColumnType(excelExportJs.eeCellTypes.Percent)));

var rows = new Array<excelExportJs.eeRow>();
var row = new excelExportJs.eeRow([
    { sNo: 1, name: '<a>Tarun</a>', age: 34, dob: '1-Nov-1983', salary: 1.11, isActive: true, marks: 0.1211 },
    { sNo: 2, name: 'Jax', age: 32, dob: { data: '5-Jan-1985', style: new excelExportJs.eeCellStyle(new excelExportJs.eeBackground('#34FFFF')) }, salary: 2.33, isActive: false, marks: 0.5422 },
    { sNo: 3, name: 'Max', age: 1, dob: { data: '15-Jun-2017', style: new excelExportJs.eeCellStyle(new excelExportJs.eeBackground('#FF0000')) }, salary: 3.44, isActive: true, marks: 0.8133 }
]);
rows.push(row);

var table = new excelExportJs.eeTable('Table 1', cols, rows);
var table2 = new excelExportJs.eeTable('Table 2', cols, rows);

var dataSet = new Array<excelExportJs.eeTable>();
dataSet.push(table);
dataSet.push(table2);

var obj = new excelExportJs.excelExport(dataSet);

var a = document.createElement("a");
a.innerText = 'Click Me';
a.href = obj.CreateExcel(true, true);
a.download = 'download.xml';
document.body.appendChild(a);
```

## Supported Browsers

* Chrome, supported in all versions
* Firefox, supported in all versions
* Microsoft Edge, supported in all versions
* Safari, supported in all versions
* Opera, supported since 7.2
* Internet Explorer, not compatible.
