
# oss-common-dependencies-spring-boot-1.4.x

以spring-boot-1.4.x为基准, 定义spring家族和第三方依赖的版本.  
这里定义的依赖可以在子项目中覆盖.  

其中spring相关的依赖主要包括:
+ spring-boot
+ spring-data-releasetrain
+ spring-io-platform
+ spring-cloud

## 如何维护pom

properties 中主要定义依赖版本, 格式为 `<${artifactId}-version>${artifactVersion}</${artifactId}-version>`, 原则上按照来源及相关性分组排序, 以便于查找.

dependencyManagement->dependencies 中定义的第三方依赖原则上要按照字典序排序以便于查找.
