# Angular-package
npm link angular library to fast developing in local environment

第一种情况，link到打包后的lib
1. ng build lib
2. 在打包后的dist目录里运行npm link

3. npm link lib
4.  "preserveSymlinks": true
参考https://willtaylor.blog/complete-guide-to-angular-libraries/

第二种情况，link到未打包的源码
1. 在lib的源码目录下运行npm link

2. npm link lib
3. "preserveSymlinks": true
4. 修改tsconfig.app.json
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
