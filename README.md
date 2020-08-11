# Angular-package
npm link angular library to fast developing in local environment

第一种情况，link到打包后的lib
1. 运行ng build lib打包angular library
2. 在打包后的dist目录里运行npm link，相当于把dist目录软链接到全局node_modules下

3. 在需要使用lib的其他Angular应用根目录下运行npm link lib
4. 在angular.json中配置 "preserveSymlinks": true ，路径 architect -> build -> options

参考https://willtaylor.blog/complete-guide-to-angular-libraries/

第二种情况，link到未打包的源码
1. 在lib的源码目录下运行npm link

2. npm link lib， 此时链接到的是ts源码
3. "preserveSymlinks": true
4. 修改tsconfig.app.json
```
    "include": [
        "*.ts",
        "*/**/*.ts",
        "../node_modules/@kpmg/questionnaire/src/**/*.ts"       // 需要手动加入ts编译的文件
    ],
    "exclude": [
        "test.ts",
        "**/*.spec.ts",
        "../node_modules/@kpmg/questionnaire/src/test.ts",
        "../node_modules/@kpmg/questionnaire/src/**/*.spec.ts"
    ]
```
