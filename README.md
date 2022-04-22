编写Plugin的代码时，settings.gradle中的`repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)`需要去掉，否则会报一个`repository 'Gradle Libs' was added by unknown code`的错误

使用插件时，把settings.gradle中的代码module在注释掉，放开储存库设置的注释，就是include的注释掉，`repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)`的注释打开

 [对于repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)这东西的说明](https://blog.csdn.net/NINO_JAM/article/details/123885693).


该插件会自动填充以下内容

```
plugins {
	...
	id("org.jetbrains.kotlin.android")
	...
}

android {
	compileSdkVersion(32)
	defaultConfig {
		it.minSdk = 21
		it.targetSdk = 32
		it.versionCode = 55
		it.versionName = "1.0"
	}
	compileOptions {
		it.sourceCompatibility(JavaVersion.VERSION_1_8)
		it.targetCompatibility(JavaVersion.VERSION_1_8)
	}
}

```
**在使用处填写这些配置，会覆盖插件中的配置**



