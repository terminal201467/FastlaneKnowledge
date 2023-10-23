# Gym

当使用 Fastlane 构建和打包 iOS 应用程序时，gym 是一个常用的 Fastlane 插件，用于执行与构建和打包相关的任务。以下是关于 gym 插件的用法和意义的总结：

意义：

gym 插件用于自动化 iOS 应用程序的构建过程。它执行以下任务：

编译应用程序：gym 使用 Xcode 或其他相关工具编译你的 iOS 应用程序源代码，将其转化为可执行的二进制文件。

生成归档：gym 生成一个应用程序的归档文件（Archive），这是一种已经编译和打包的应用程序，用于后续的分发或提交到 App Store。

自动签名：gym 可以自动签名你的应用程序，以便后续的部署和分发。

用法：

以下是使用 gym 插件的常见用法和配置选项：

```
lane :build_and_archive do
  gym(
    # 以下是常用的配置选项
    scheme: "MyApp",            # 应用程序的 scheme 名称
    configuration: "Release",  # 使用的构建配置，通常是 Release
    export_method: "app-store", # 导出方法，可选值包括 "app-store"、"ad-hoc"、"development" 等
    export_options: {
      uploadBitcode: false,     # 是否上传 Bitcode
      uploadSymbols: false,     # 是否上传符号
      provisioningProfiles: {
        "com.example.app": "Profile Name"
      }
    }
  )
end

```
scheme：指定你的应用程序的 scheme 名称。
configuration：通常设置为 "Release"，表示使用 Release 构建配置。
export_method：指定导出方法，常用选项包括 "app-store"（用于提交到 App Store）和 "ad-hoc"（用于 Ad-Hoc 分发）。
export_options：一个包含导出选项的哈希表，用于进一步配置构建行为。你可以控制是否上传 Bitcode、上传符号、设置 provisioning profiles 等。
通过使用 gym 插件，你可以轻松地将构建和归档应用程序的任务自动化，无需手动执行复杂的构建步骤。这有助于提高工作流的效率，并减少人为错误。
