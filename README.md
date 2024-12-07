## About

**metal-cpp** is a low overhead and header only C++ interface for Metal that helps developers add Metal functionality to graphics applications that are written in C++ (such as game engines). **metal-cpp** removes the need to create a shim and allows developers to call Metal functions directly from anywhere in their existing C++ code.

仓库中的代码依据 [官方](https://developer.apple.com/metal/cpp/) metal-cpp_macOS15_iOS18.zip 版本修改而来。

## 使用

`CMakeLists.txt` 中

```
find_package(metal-cpp CONFIG REQUIRED)

add_executable(MetalPractice metal_practice.cc)

target_compile_features(MetalPractice PRIVATE cxx_std_20)

target_link_libraries(MetalPractice PRIVATE metal-cpp::metal-cpp)
```

`vcpkg.json` 中添加

```json
"registries": [
    {
      "kind": "git",
      "repository": "https://github.com/hollykbuck/vcpkg_registry",
      "reference": "main",
      "baseline": "9a433047996b4ae6d92130c08d5e8e2259b3216c",
      "packages": [
        "metal-cpp", "metal-cpp-extensions"
      ]
    }
]
```

建议将 baseline 替换为 [hollykbuck/vcpkg_registry](https://github.com/hollykbuck/vcpkg_registry) 最新 commit。

## 联动

[metal-cpp](https://developer.apple.com/metal/cpp/) 官方版本
[hollykbuck/metal-cpp](https://github.com/hollykbuck/metal-cpp) 我打包的版本
[hollykbuck/vcpkg_registry](https://github.com/hollykbuck/vcpkg_registry) vcpkg 个人仓库