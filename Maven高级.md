# 1. 分模块开发

拆分模块后只需要在主项目 pom 文件里加入拆分出的项目的 pom 文件中的坐标，再把拆分出的项目在 Maven 界面 install 打包进仓库即可。如果拆分出的项目需要主项目的部分文件，重复上述即可。



## 1.1 依赖传递

![image-20240306135859960](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240306135859960.png)

后配置指写在靠后位置



## 1.2 可选依赖和排除依赖

![image-20240306140940955](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240306140940955.png)

设置为 false 后其他项目引用后则看不见这个依赖



![image-20240306140915693](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240306140915693.png)



## 1.3 聚合

![image-20240306141149430](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240306141149430.png)

  聚合工程是一个空的工程，一般只有一个pom文件，里面装着各个模块的地址，创建时选择Maven模块，设置打包类型为pom。

![image-20240311094035581](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311094035581.png)

## 1.4 继承

子工程可以继承父工程中的依赖。可以用聚合工程作总父工程。

可选依赖要在子工程中写上依赖（不用写版本号）才能使用。

![image-20240311095135312](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311095135312.png)

![image-20240311095150276](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311095150276.png)

![image-20240311095252473](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311095252473.png)

![image-20240311095303633](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311095303633.png)

## 1.5 属性

![image-20240311095548310](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311095548310.png)

![image-20240311095559468](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311095559468.png)

## 1.6 私服

