# Install via Package Manager
ubuntu
[see Github page of nodesource](https://github.com/nodesource/distributions/blob/master/README.md)
>curl -fsSL https://deb.nodesource.com/setup_19.x | sudo -E bash - &&\ 
>sudo apt-get install -y nodejs`

check if successfully installed (and version)
`node -v`
`npm -v`
*npm is package manager of node




## Downloading via npm
`npm insatll xxx -g`: global
`npm install xxx -S`: local, create environment ***
`npm install xxx -D`: local, development environment

`npm i express -S`: download express module
`npm i mysql -S`: download mysql module
* `package.json`: description-file of project
* 

npm login (*I don't see a reason to do that

open html from terminal:
`browsername filename`


server.listen(8080);
url require path
`req.url`
url 
`const url = require(url");`
`url.parse(reqUrl,true).query


post: receive stuff
`req.on('data')`:send data
`req.on('end')`:data sending is done

querystring: to change format (or split it...?)


## Connection to MySQL
1. download mysql module (in the dir that contains server.js)
   `npm install mysql`
2. import mysql
   in server.js:
   `const mysql = require("mysql");`
3. config
   

## Import local CSV file into MySQL with NodeJS
`fast-csv` for reading csv. file, and `mysql` of course
1. `npm install fast-csv`
2. 

```
CREATE TABLE mytable(
   lfdNr          INTEGER  NOT NULL PRIMARY KEY 
  ,Gruppe         VARCHAR(33) NOT NULL
  ,Platz          VARCHAR(3) NOT NULL
  ,Matrikelnummer INTEGER  NOT NULL
  ,Abschlussziel  VARCHAR(12) NOT NULL
  ,SPOVersion     VARCHAR(76) NOT NULL
  ,StudienID      VARCHAR(13) NOT NULL
  ,Studium        VARCHAR(36) NOT NULL
  ,Fachsemester   INTEGER  NOT NULL
  ,Anmeldedatum   VARCHAR(16) NOT NULL
  ,Kennzahl       VARCHAR(11) NOT NULL
);
```














## nicht wichtig (or: haven't translated)
*Guideline: CommenJS 
* 每个文件都是一个模块，都有自己的作用域
* 在模块内部，module变量代表自身
* module.exports提供对外接口
*require
* /代表绝对路径 ./代表相对路径
* /默认后缀： js json node
* require('http') ==>node_modules
*global (全局对象)