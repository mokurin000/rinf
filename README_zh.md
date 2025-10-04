# Rinf: Rust in Flutter

[![Pub Version](https://img.shields.io/pub/v/rinf)](https://pub.dev/packages/rinf)
[![Crate Version](https://img.shields.io/crates/v/rinf)](https://crates.io/crates/rinf)
[![GitHub Stars](https://img.shields.io/github/stars/cunarist/rinf)](https://github.com/cunarist/rinf/stargazers)
[![Test App](https://github.com/cunarist/rinf/actions/workflows/test_app.yaml/badge.svg)](https://github.com/cunarist/rinf/actions/workflows/test_app.yaml?query=branch%3Amain)
[![GitHub License](https://img.shields.io/github/license/cunarist/rinf)](https://github.com/cunarist/rinf/blob/main/LICENSE)

**Rust 处理原生业务逻辑, Flutter 打造灵活美观的图形界面**

![Preview](https://github.com/cunarist/rinf/assets/66480156/5c9a7fb6-e566-4c4e-bd77-d72c1c064d6c)

Rinf 是一个框架，可通过使用 Flutter 作为UI层，创建美观且高性能的跨平台Rust应用程序。只需将此框架添加到您的应用程序项目中，即可轻松在Flutter中调用Rust代码！

## 📖 文档

开始学习使用本框架，请阅读[文档](https://rinf.cunarist.com)。你也可以浏览[样例代码](https://github.com/cunarist/rinf/tree/main/flutter_package/example)。

## 🖥️ 平台支持

所有Flutter支持的平台均已[测试](https://github.com/cunarist/rinf/actions/workflows/test_app.yaml?query=branch%3Amain)支持。额外的构建配置都会被该框架自动处理。

- ✅ Linux: 测试支持
- ✅ Android:  测试支持
- ✅ Windows:  测试支持
- ✅ macOS:  测试支持
- ✅ iOS:  测试支持
- ✅ Web:  测试支持
- 🔄 [eLinux](https://github.com/sony/flutter-elinux): 实验性

## 📞 交互

下面是 Rust 代码实现的业务逻辑，和 Dart 代码实现组件。

```rust
MyMessage {
  current_number: 7,
  other_bool: true,
}
.send_signal_to_dart();
```

```dart
StreamBuilder(
  stream: MyMessage.rustSignalStream,
  builder: (context, snapshot) {
    final signalPack = snapshot.data;
    if (signalPack == null) {
      return Text('Nothing received yet');
    }
    final myMessage = signalPack.message;
    return Text(myMessage.currentNumber.toString());
  },
)
```

从 Dart 往 Rust 通信也可以以类似形式完成。

所有的 Dart 类会被 Rinf 生成为类型安全的形式。你可以通过派生Trait定义消息 schema。

## 🎁 优势

- **简单**: 只需要一二分钟，就可以完全搭建好你的app。
- **高效**: 所有的通信都完全通过原生FFI实现。没有Webview，网络服务器，隐藏线程，或者不必要的内存复制等导致额外开销。Rinf 会进行尽可能轻的交互包装。
- **最小化**: Rinf 是一个轻量的的框架，不需要你安装很多依赖或使用复杂的命令行工具。你只需要关注基于你在Rust/Flutter侧喜欢的库的代码。
- **事件驱动**: Rinf 异步系统可响应用户动作、消息、信号等事件，从而实现了高级并发处理、任务取消机制和非阻塞业务逻辑。
- **可拓展**: 在 Dart 与 Rust 之间创建成百上千个消息接口，依然能保持简洁流畅。更重要的是，你可以灵活调用任何 Rust 库，包括你已经使用过的。
- **High-level interface**: No messing with sensitive build files, no concerns about memory safety. Stay with Dart and Rust that you're familiar with.
- **Well maintained**: Our [automated workflows](https://github.com/cunarist/rinf/actions) including build tests are always kept passing, thanks to the main branch protection rule. Also, the number of external dependencies is kept as low as possible and documentations are thoughtfully organized.
- **Convenient debugging**: All the debugging functionalities are provided by default, without the need for dealing with browsers or mobile emulators. Also, the whole Rust logic is automatically restarted on Dart's hot restart.
- **Reliable**: Each component is supported by huge communities, ensuring a strong emphasis on future safety. You can easily assure your team of stability since this framework's underlying concept is fairly simple.

## 🐦 Why Use Flutter?

While Rust is a powerful language for high-performance native programming, its ecosystem for building graphical user interfaces is far from being mature. Though Rust already has some GUI frameworks, they don't compare to the extensive support and smooth development experience that Flutter provides. Flutter is the only framework that compiles to all six major platforms from a single codebase.

Flutter is a powerful and versatile framework that has gained immense popularity for building cross-platform applications with stunning user interfaces. It provides a declarative pattern, beautiful widgets, hot reload, convenient debugging tools, and dedicated packages for user interfaces right out of the box.

## 🦀 Why Use Rust?

While Dart excels as an amazing object-oriented language for GUI apps, its non-native garbage collection may not always meet demanding performance requirements, and it may lack advanced data manipulation packages. This is where Rust steps in, offering a remarkable speed advantage of up to [40 times faster](https://programming-language-benchmarks.vercel.app/dart-vs-rust) than Dart, alongside the ability to leverage multiple threads and various crates that get the job done.

Rust has garnered a devoted following, being [the most loved programming language](https://survey.stackoverflow.co/2022#section-most-loved-dreaded-and-wanted-programming-scripting-and-markup-languages) on Stack Overflow. Its native performance, thanks to the zero-cost abstraction philosophy, ensures high productivity. Many developers foresee Rust potentially replacing C++ in the future. Rust's simplicity, memory safety, superior performance in various scenarios, vibrant community, and robust tooling support contribute to its growing popularity.

## 👥 Contribution

If Rinf has been helpful, please consider giving a star to our [GitHub repository](https://github.com/cunarist/rinf) and a like to our [Pub package](https://pub.dev/packages/rinf). You can also support us by spreading the word and sharing this framework online.

We appreciate your contribution to the development of this project! We're always open to discussions and pull requests, so please do not hesitate to share your ideas or opinions on our GitHub repository.

[![GitHub contributors](https://contrib.rocks/image?repo=cunarist/rinf)](https://github.com/cunarist/rinf/graphs/contributors)
