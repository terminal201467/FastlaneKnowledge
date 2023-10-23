# 上架

# 请确保已经设置好环境变量或 Fastfile 中的相关配置，包括 Apple ID 和 Team ID

```
lane :upload_to_testflight do
```
  # 执行构建和打包

```
  gym(
    # 指定项目、配置等参数
    scheme: "YourAppScheme",
    export_method: "ad-hoc"
  )

  # 上传到 TestFlight
  pilot(
    # 你的 Apple ID
    username: "your_email@example.com",
    
    # 如果你使用不同的分组进行测试，可以指定分组名称
    groups: ["Testers"],
    
    # 上传的二进制文件路径
    ipa: "./path/to/your/app.ipa",
    
    # 你可以选择是否进行提交审核
    submit_for_review: true
  )
end
```

