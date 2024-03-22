**注：MP可能还不能支持SpringBoot3.x**

可以省略若干dao层sql的写

# 1.MyBatisPlus入门

![image-20240311104439952](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311104439952.png)

![image-20240311104449241](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311104449241.png)

   ![image-20240311104512514](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311104512514.png)

现在可能已经有了

![image-20240311104532763](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311104532763.png)

![image-20240311104555026](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311104555026.png)

![image-20240311104609464](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311104609464.png)

继承BassMapper<User>后大多数简单的sql都可以直接使用了

![image-20240311104654024](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311104654024.png)



# 2. MyBatisPlus 标准数据层开发

## 2.1 标准数据层CRUD功能

![image-20240311105650427](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311105650427.png)

其实就是帮你把dao层的sql写完了，直接用就行。



### 2.1.1 lombok 实体类注释（简化getter、setter之类）

![image-20240311105814814](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311105814814.png)

![image-20240311105848238](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311105848238.png)



## 2.2 标准分页功能开发

![image-20240311110644524](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311110644524.png)

在config下设置

![image-20240311110736964](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311110736964.png)

![image-20240311110749108](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311110749108.png)

调试用，在resource中设置，设置后输出会附带sql信息。



# 3. DQL编程控制

## 3.1 条件查询方式

![image-20240311135713261](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311135713261.png)

![image-20240311135747757](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311135747757.png)

![image-20240311135810946](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311135810946.png)



## 3.2 null值处理

![image-20240311140643251](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311140643251.png)

相当于

![image-20240311140706253](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311140706253.png)

建议下面这种



## 3.3 查询投影（设置要查询的数据字段）

![image-20240311141422390](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311141422390.png)

如果太麻烦的查询投影还是用会mybatis的map映射吧



## 3.4 查询条件设置（> 、=、between、like、null、in、group、order）

**lt 小于 -- le 小于等于**

**gt 大于 -- ge 大于等于**

**eq 等于**

**between** **之间（闭区间）**

**likeLeft %查询条件**

**likeRight 查询条件%**



其余查询MybatisPlus条件构造器

https://blog.csdn.net/Huang_ZX_259/article/details/122524602

## 3.5 数据库字段与实体类属性映射匹配

![image-20240311143146148](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311143146148.png)

如当数据库中的字段名为pwd时



![image-20240311143310710](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311143310710.png)

如在实体类中添加数据库中没有的属性



![image-20240311143445421](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311143445421.png)

 如查询时选定字段不参与查询



![image-20240311143546780](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311143546780.png)

如表名与实体类名不一样



# 4.DML编程控制

## 4.1 新增时id生成策略控制

  ![image-20240311145934872](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311145934872.png)

在实体类中进行设置

![image-20240311145440767](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311145440767.png)

雪花算法算出的数据格式：64位2进制--long型

![image-20240311145633257](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311145633257.png)

也可以转到application.yml中进行全局配置

![image-20240311150105385](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311150105385.png)

像这样把@TableName(“tbl_xxx”)进行简化，tbl_可以不写

```yml
mybatis-plus:
  global-config:
    db-config:
      id-type: assign_id
```

像这样就可以把@TableId(type = xxx)省去



## 4.2 多条数据删除 

![image-20240311150922483](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311150922483.png)



## 4.3 逻辑删除

![image-20240311151221648](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311151221648.png)

![image-20240311151609638](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311151609638.png)

![image-20240311151624391](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311151624391.png)

![image-20240311151636418](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311151636418.png)

相比2更推荐3

![image-20240311151737776](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311151737776.png)

## 4.4 乐观锁

![image-20240311153358693](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311153358693.png)

![image-20240311153409592](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311153409592.png)

![image-20240311153421958](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311153421958.png)

![image-20240311153431978](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311153431978.png)



# 5. 代码生成器

![image-20240311163050648](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240311163050648.png)

详情见：

https://www.bilibili.com/video/BV1Fi4y1S7ix/?p=118&spm_id_from=pageDriver&vd_source=542979c6bdb106fd23293c7648d31688
