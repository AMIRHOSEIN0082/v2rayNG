# [v2rayNG](https://github.com/2dust/v2rayNG)

**Compile the APK file for v2rayNG using the latest commit code from Xray-core and the latest version of go in order to test some features.**

# Generate apk signing certificate with keytool

1. Download [**JDK Development Kit**](https://download.oracle.com/java/20/latest/jdk-20_windows-x64_bin.zip).

2. Unzip the file, right-click in the `\bin` folder, select Open in Terminal, and paste the command in the Command Prompt window.

```
keytool -genkey -v -keystore keystore.jks -alias chika -storepass lovelive -keypass lovelive -validity 365 -keyalg RSA -keysize 2048
```

Replace `-alias chika` `-storepass lovelive` `-keypass lovelive` `-validity 365` with your values.

3. Upload the generated **keystore.jks** file to your VPS and paste the command in the SSH terminal.

```
openssl base64 < keystore.jks | tr -d '\n' | tee keystore_base64.txt
```

4. After forking this repository, click `Settings` -> `Secrets and Variables` -> `Options` -> `New Repository Secret`.

5. Add the following new item, replacing it with your value.

| Name | Secret |
| :--- | :--- |
| ALIAS | `chika` |
| KEYPASSWORD | `lovelive` |
| KEYSTOREPASSWORD | `lovelive` |
| SIGNINGKEYBASE64 | `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` |

# 使用keytool生成apk签名证书

1. 下载 [**JDK Development Kit**](https://download.oracle.com/java/20/latest/jdk-20_windows-x64_bin.zip)。

2. 解压后在 `\bin` 文件夹中点击右键，选择在终端中打开，在命令提示符窗口中粘贴命令。

```
keytool -genkey -v -keystore keystore.jks -alias chika -storepass lovelive -keypass lovelive -validity 365 -keyalg RSA -keysize 2048
```

将 `-alias chika` `-storepass lovelive` `-keypass lovelive` `-validity 365` 替换成你的值。

3. 将生成的 **keystore.jks** 文件上传到你的VPS，在SSH终端中粘贴命令。

```
openssl base64 < keystore.jks | tr -d '\n' | tee keystore_base64.txt
```

4. Fork本仓库后，点击 `Settings` —> `Secrets and variables` —> `Actions` —> `New repository secret`。

5. 新增以下项目，替换成你的值。

| Name | Secret |
| :--- | :--- |
| ALIAS | `chika` |
| KEYPASSWORD | `lovelive` |
| KEYSTOREPASSWORD | `lovelive` |
| SIGNINGKEYBASE64 | `粘贴 keystore_base64.txt 中的内容` |
