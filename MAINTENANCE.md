# Adding New Functionality from the Yandex.Games SDK

Developing new functionality for Defold is relatively straightforward. Your primary focus should be on four files:

- `ysdk/src/ysdk.cpp`: Here, you can declare new tables and functions for Lua.
- `ysdk/include/ysdk.h`: If necessary, you can declare `externs` here for interacting with JavaScript.
- `ysdk/lib/web/library_ysdk.js`: This is where you write code that interacts with the Yandex.Games SDK.
- `ysdk/api/ysdk.script_api`: This YAML file contains information for adding [Auto-complete](https://defold.com/manuals/extensions-script-api/) support to your new methods.

The code is organized to ensure that game developers can easily work with the SDK using callback functions, while you, as the plugin developer, can conveniently add new functionality using `dmScript::CreateCallback` in C++ and `makeDynCall` from Emscripten.

Yandex.Games SDK often involves adding asynchronous I/O methods. Their implementation is fairly simple, and you can find numerous examples in this repository for various use cases.

However, exceptions like the event system [`ysdk.on`](https://yandex.ru/dev/games/doc/ru/sdk/sdk-events) require more complex interaction between Lua and JavaScript.

### Learning materials:
- [Emscripten Documentation](https://emscripten.org/)  
- [The "Native Extensions" section in the Defold documentation](https://defold.com/manuals/extensions/)  
- [SDK Script API (dmScript) Documentation](https://defold.com/ref/dmScript/)  
- [Lua Manual](https://www.lua.org/manual/5.4/)

# Releasing a New Version

After making all the necessary changes, you need to release a new version of the extension. To do this:

1. Reflect all your changes in the `CHANGELOG.md` file.
2. Go to GitHub and create a new release.
3. Make sure to include the information from `CHANGELOG.md` in the release description.
