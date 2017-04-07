
# 技术栈依赖管理

定义技术栈的全部软件依赖.  

现代软件通常会依赖大量开源软件, 这些开源软件还依赖其它开源软件, 依赖关系比较复杂, 如果使用了错误的依赖可能导致隐蔽的运行时错误.
oss-common-dependencies就是为了解决依赖管理的难题, 为oss及其用户构建一个稳定的依赖版本基线, 然后在这些依赖的基础上构建可靠的软件.  

你的项目应该使用oss-release, oss-release包括oss-common-dependencies和oss-lib.  
oss-lib项目使用oss-common-dependencies来定义依赖.  

[oss-lib](http://gitlab.internal/infra/oss-lib)提供易于使用的库, 直接使用oss-common-dependencies进行依赖管理.  
[oss-release](http://gitlab.internal/infra/oss-release)整合oss-common-dependencies和oss-lib.  


你的项目可以使用oss-release作为parent, 这样间接地以oss-build为ancestor.

    <parent>
        <groupId>com.yirendai.oss</groupId>
        <artifactId>oss-release-spring-boot-${spring-boot.version}</artifactId>
        <version>${oss-release.version}</version>
    </parent>

或者在dependencyManagement中import它.

    <!-- 以oss-build为parent是可选的 -->
    <parent>
        <groupId>com.yirendai.oss</groupId>
        <artifactId>oss-build</artifactId>
        <version>${oss-build.version}</version>
    </parent>
    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>com.yirendai.oss</groupId>
                <artifactId>oss-release-spring-boot-${spring-boot.version}</artifactId>
                <version>${oss-release.version}</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
        </dependencies>
    </dependencyManagement>
