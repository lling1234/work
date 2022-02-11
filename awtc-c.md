.h是头文件，一般存放**函数的声明、数组、和定义的变量**，

.c是源文件，是实现函数程序的功能，linux下 .o是编译之后的二进制文件，

.s是汇编，汇编代码；.S 预处理+汇编

.o是object，也就相当于Windows下编译的obj文件，俗称目标文件。

.a 就是archive, 也就相当于windows的VC下编译的lib文件, 俗称静态库文件。

.so是动态库。 如果您使用存储在其中的代码，则不会将其嵌入到您自己的二进制文件中。 相反它只是被引用，所以二进制文件将取决于它们，并且so文件中的代码在运行时添加/加载。 在Visual Studio / Windows中，这些将是.dll文件（包含链接信息的小.lib文件）。

extern可以置于变量或者[函数](http://www.bc-cn.net/Article/Search.asp?Field=Title&ClassID=&keyword=%BA%AF%CA%FD)前，以标示变量或者**[函数](http://www.bc-cn.net/Article/Search.asp?Field=Title&ClassID=&keyword=%BA%AF%CA%FD)的定义在别的文件中**，提示编译器遇到此变量和[函数](http://www.bc-cn.net/Article/Search.asp?Field=Title&ClassID=&keyword=%BA%AF%CA%FD)时**在其他模块中寻找其定义**。

 static 的最主要功能是**隐藏**，其次因为 static 变量存放在静态存储区，所以它具备持久性和默认值0。

make、Scons、CMake编译工具

Linux下CMake简明教程https://blog.csdn.net/whahu1989/article/details/82078563

**防止头文件的重复包含和编译** #ifndef    #define

一、编译的四个阶段
预处理：编译处理宏定义等宏命令（eg:#define）——生成后缀为“.i”的文件 　　
编译：将预处理后的文件转换成汇编语言——生成后缀为“.s”的文件 　　
汇编：由汇编生成的文件翻译为二进制目标文件——生成后缀为“.o”的文件 　　
链接：多个目标文件（二进制）结合库函数等综合成的能直接独立执行的执行文件——生成后缀为“.out”的文件

#### gcc 与g++的区别

1、对于不同后缀的文件当作程序不同。

c后缀的文件，gcc把它当做是C程序；g++当做是C++程序；对于.cpp后缀的文件，gcc和g++都会当做c++程序。

2、编译阶段调用不同，g++会调用gcc;

3、链接阶段方式不同，通常会用g++来完成，这是因为gcc命令不能自动和c++程序使用的库连接。

4、gcc和g++都可以编译c和cpp，需要加参数。



```bash
chen_yixuan@Ubuntu01:~/awtk/awtk-examples/HelloDesigner-Demo$ scons
scons: Reading SConscript files ...
APP_SCRIPTS_ROOT:/home/chen_yixuan/awtk/awtk-examples/HelloDesigner-Demo/scripts
AWTK_ROOT: /home/chen_yixuan/awtk/awtk
AWTK_SCRIPTS_ROOT: /home/chen_yixuan/awtk/awtk/scripts
MACH=x86_64 ARCH=('64bit', 'ELF') TARGET_ARCH=
TK_ROOT: /home/chen_yixuan/awtk/awtk
WIN32_AWTK_RES: /home/chen_yixuan/awtk/awtk/win32_res/awtk.res
False
800 480
AWTK_ROOT: /home/chen_yixuan/awtk/awtk
{'SHARED': 'False', 'IDL_DEF': 'False'}
scons: done reading SConscript files.
scons: Building targets ...
gcc -o src/app_main.o -c -std=gnu99 -DLCD_WIDTH=800 -DLCD_HEIGHT=480 -DAPP_DEFAULT_FONT=\"default\" -DAPP_THEME=\"default\" -DAPP_RES_ROOT="\"../res\"" -DAPP_DEFAULT_LANGUAGE=\"en\" -DAPP_DEFAULT_COUNTRY=\"US\" -DAPP_ROOT="\"/home/chen_yixuan/awtk/awtk-examples/HelloDesigner-Demo\"" -g -Wall -Wno-unused-function -fPIC -DWITH_64BIT_CPU -DTK_ROOT="\"/home/chen_yixuan/awtk/awtk\"" -DWITH_MBEDTLS=1 -DENABLE_CURSOR=1 -DWITH_TEXT_BIDI=1 -DWITH_DATA_READER_WRITER=1 -DWITH_EVENT_RECORDER_PLAYER=1 -DWITH_ASSET_LOADER -DWITH_FS_RES -DWITH_ASSET_LOADER_ZIP -DSTBTT_STATIC -DSTB_IMAGE_STATIC -DWITH_STB_IMAGE -DWITH_VGCANVAS -DWITH_UNICODE_BREAK -DWITH_DESKTOP_STYLE -DWITH_SDL -DHAS_STDIO -DHAVE_STDIO_H -DHAS_GET_TIME_US64 -DHAS_STD_MALLOC -DTK_MAX_MEM_BLOCK_NR=3 -DWITH_IME_PINYIN -DWITH_NANOVG_GPU -DWITH_VGCANVAS_LCD -DWITH_STB_FONT -DWITH_NANOVG_GL3 -DWITH_NANOVG_GL -DLINUX -DHAS_PTHREAD -DSDL_REAL_API -DSDL_TIMER_UNIX -DSDL_VIDEO_DRIVER_X11 -DSDL_VIDEO_DRIVER_X11_SUPPORTS_GENERIC_EVENTS -DSDL_AUDIO_DRIVER_SNDIO -DSDL_VIDEO_OPENGL_GLX -DSDL_VIDEO_RENDER_OGL -DSDL_LOADSO_DLOPEN -DSDL_VIDEO_OPENGL_EGL -DSDL_VIDEO_OPENGL_ES2 -DSDL_REAL_API -DSDL_HAPTIC_DISABLED -DSDL_SENSOR_DISABLED -DSDL_JOYSTICK_DISABLED -DWITH_WIDGET_TYPE_CHECK=1 -DWITH_AWTK=1 -I/home/chen_yixuan/awtk/awtk -I/home/chen_yixuan/awtk/awtk/src -I/home/chen_yixuan/awtk/awtk/3rd -I/home/chen_yixuan/awtk/awtk/src/ext_widgets -I/home/chen_yixuan/awtk/awtk/src/custom_widgets -I/home/chen_yixuan/awtk/awtk/3rd/fribidi -I/home/chen_yixuan/awtk/awtk/3rd/mbedtls/include -I/home/chen_yixuan/awtk/awtk/3rd/mbedtls/3rdparty/everest/include -I/home/chen_yixuan/awtk/awtk/3rd/pixman -I/home/chen_yixuan/awtk/awtk/3rd/cairo -I/home/chen_yixuan/awtk/awtk/3rd/bgfx/bgfx/include -I/home/chen_yixuan/awtk/awtk/3rd/bgfx/bx/include -I/home/chen_yixuan/awtk/awtk/3rd/bgfx/bimg/include -I/home/chen_yixuan/awtk/awtk/3rd/agge -I/home/chen_yixuan/awtk/awtk/3rd/agg/include -I/home/chen_yixuan/awtk/awtk/3rd/nanovg -I/home/chen_yixuan/awtk/awtk/3rd/nanovg/gl -I/home/chen_yixuan/awtk/awtk/3rd/nanovg/base -I/home/chen_yixuan/awtk/awtk/3rd/nanovg/agge -I/home/chen_yixuan/awtk/awtk/3rd/nanovg/bgfx -I/home/chen_yixuan/awtk/awtk/3rd/SDL/src -I/home/chen_yixuan/awtk/awtk/3rd/SDL/include -I/home/chen_yixuan/awtk/awtk/3rd/agge/src -I/home/chen_yixuan/awtk/awtk/3rd/agge/include -I/home/chen_yixuan/awtk/awtk/3rd/gpinyin/include -I/home/chen_yixuan/awtk/awtk/3rd/libunibreak -I/home/chen_yixuan/awtk/awtk/3rd/gtest/googletest -I/home/chen_yixuan/awtk/awtk/3rd/gtest/googletest/include -I/home/chen_yixuan/awtk/awtk/tools -Isrc -Ires src/app_main.c
gcc -o src/window_animator.o -c -std=gnu99 -DLCD_WIDTH=800 -DLCD_HEIGHT=480 -DAPP_DEFAULT_FONT=\"default\" -DAPP_THEME=\"default\" -DAPP_RES_ROOT="\"../res\"" -DAPP_DEFAULT_LANGUAGE=\"en\" -DAPP_DEFAULT_COUNTRY=\"US\" -DAPP_ROOT="\"/home/chen_yixuan/awtk/awtk-examples/HelloDesigner-Demo\"" -g -Wall -Wno-unused-function -fPIC -DWITH_64BIT_CPU -DTK_ROOT="\"/home/chen_yixuan/awtk/awtk\"" -DWITH_MBEDTLS=1 -DENABLE_CURSOR=1 -DWITH_TEXT_BIDI=1 -DWITH_DATA_READER_WRITER=1 -DWITH_EVENT_RECORDER_PLAYER=1 -DWITH_ASSET_LOADER -DWITH_FS_RES -DWITH_ASSET_LOADER_ZIP -DSTBTT_STATIC -DSTB_IMAGE_STATIC -DWITH_STB_IMAGE -DWITH_VGCANVAS -DWITH_UNICODE_BREAK -DWITH_DESKTOP_STYLE -DWITH_SDL -DHAS_STDIO -DHAVE_STDIO_H -DHAS_GET_TIME_US64 -DHAS_STD_MALLOC -DTK_MAX_MEM_BLOCK_NR=3 -DWITH_IME_PINYIN -DWITH_NANOVG_GPU -DWITH_VGCANVAS_LCD -DWITH_STB_FONT -DWITH_NANOVG_GL3 -DWITH_NANOVG_GL -DLINUX -DHAS_PTHREAD -DSDL_REAL_API -DSDL_TIMER_UNIX -DSDL_VIDEO_DRIVER_X11 -DSDL_VIDEO_DRIVER_X11_SUPPORTS_GENERIC_EVENTS -DSDL_AUDIO_DRIVER_SNDIO -DSDL_VIDEO_OPENGL_GLX -DSDL_VIDEO_RENDER_OGL -DSDL_LOADSO_DLOPEN -DSDL_VIDEO_OPENGL_EGL -DSDL_VIDEO_OPENGL_ES2 -DSDL_REAL_API -DSDL_HAPTIC_DISABLED -DSDL_SENSOR_DISABLED -DSDL_JOYSTICK_DISABLED -DWITH_WIDGET_TYPE_CHECK=1 -DWITH_AWTK=1 -I/home/chen_yixuan/awtk/awtk -I/home/chen_yixuan/awtk/awtk/src -I/home/chen_yixuan/awtk/awtk/3rd -I/home/chen_yixuan/awtk/awtk/src/ext_widgets -I/home/chen_yixuan/awtk/awtk/src/custom_widgets -I/home/chen_yixuan/awtk/awtk/3rd/fribidi -I/home/chen_yixuan/awtk/awtk/3rd/mbedtls/include -I/home/chen_yixuan/awtk/awtk/3rd/mbedtls/3rdparty/everest/include -I/home/chen_yixuan/awtk/awtk/3rd/pixman -I/home/chen_yixuan/awtk/awtk/3rd/cairo -I/home/chen_yixuan/awtk/awtk/3rd/bgfx/bgfx/include -I/home/chen_yixuan/awtk/awtk/3rd/bgfx/bx/include -I/home/chen_yixuan/awtk/awtk/3rd/bgfx/bimg/include -I/home/chen_yixuan/awtk/awtk/3rd/agge -I/home/chen_yixuan/awtk/awtk/3rd/agg/include -I/home/chen_yixuan/awtk/awtk/3rd/nanovg -I/home/chen_yixuan/awtk/awtk/3rd/nanovg/gl -I/home/chen_yixuan/awtk/awtk/3rd/nanovg/base -I/home/chen_yixuan/awtk/awtk/3rd/nanovg/agge -I/home/chen_yixuan/awtk/awtk/3rd/nanovg/bgfx -I/home/chen_yixuan/awtk/awtk/3rd/SDL/src -I/home/chen_yixuan/awtk/awtk/3rd/SDL/include -I/home/chen_yixuan/awtk/awtk/3rd/agge/src -I/home/chen_yixuan/awtk/awtk/3rd/agge/include -I/home/chen_yixuan/awtk/awtk/3rd/gpinyin/include -I/home/chen_yixuan/awtk/awtk/3rd/libunibreak -I/home/chen_yixuan/awtk/awtk/3rd/gtest/googletest -I/home/chen_yixuan/awtk/awtk/3rd/gtest/googletest/include -I/home/chen_yixuan/awtk/awtk/tools -Isrc -Ires src/window_animator.c
gcc -o src/window_background.o -c -std=gnu99 -DLCD_WIDTH=800 -DLCD_HEIGHT=480 -DAPP_DEFAULT_FONT=\"default\" -DAPP_THEME=\"default\" -DAPP_RES_ROOT="\"../res\"" -DAPP_DEFAULT_LANGUAGE=\"en\" -DAPP_DEFAULT_COUNTRY=\"US\" -DAPP_ROOT="\"/home/chen_yixuan/awtk/awtk-examples/HelloDesigner-Demo\"" -g -Wall -Wno-unused-function -fPIC -DWITH_64BIT_CPU -DTK_ROOT="\"/home/chen_yixuan/awtk/awtk\"" -DWITH_MBEDTLS=1 -DENABLE_CURSOR=1 -DWITH_TEXT_BIDI=1 -DWITH_DATA_READER_WRITER=1 -DWITH_EVENT_RECORDER_PLAYER=1 -DWITH_ASSET_LOADER -DWITH_FS_RES -DWITH_ASSET_LOADER_ZIP -DSTBTT_STATIC -DSTB_IMAGE_STATIC -DWITH_STB_IMAGE -DWITH_VGCANVAS -DWITH_UNICODE_BREAK -DWITH_DESKTOP_STYLE -DWITH_SDL -DHAS_STDIO -DHAVE_STDIO_H -DHAS_GET_TIME_US64 -DHAS_STD_MALLOC -DTK_MAX_MEM_BLOCK_NR=3 -DWITH_IME_PINYIN -DWITH_NANOVG_GPU -DWITH_VGCANVAS_LCD -DWITH_STB_FONT -DWITH_NANOVG_GL3 -DWITH_NANOVG_GL -DLINUX -DHAS_PTHREAD -DSDL_REAL_API -DSDL_TIMER_UNIX -DSDL_VIDEO_DRIVER_X11 -DSDL_VIDEO_DRIVER_X11_SUPPORTS_GENERIC_EVENTS -DSDL_AUDIO_DRIVER_SNDIO -DSDL_VIDEO_OPENGL_GLX -DSDL_VIDEO_RENDER_OGL -DSDL_LOADSO_DLOPEN -DSDL_VIDEO_OPENGL_EGL -DSDL_VIDEO_OPENGL_ES2 -DSDL_REAL_API -DSDL_HAPTIC_DISABLED -DSDL_SENSOR_DISABLED -DSDL_JOYSTICK_DISABLED -DWITH_WIDGET_TYPE_CHECK=1 -DWITH_AWTK=1 -I/home/chen_yixuan/awtk/awtk -I/home/chen_yixuan/awtk/awtk/src -I/home/chen_yixuan/awtk/awtk/3rd -I/home/chen_yixuan/awtk/awtk/src/ext_widgets -I/home/chen_yixuan/awtk/awtk/src/custom_widgets -I/home/chen_yixuan/awtk/awtk/3rd/fribidi -I/home/chen_yixuan/awtk/awtk/3rd/mbedtls/include -I/home/chen_yixuan/awtk/awtk/3rd/mbedtls/3rdparty/everest/include -I/home/chen_yixuan/awtk/awtk/3rd/pixman -I/home/chen_yixuan/awtk/awtk/3rd/cairo -I/home/chen_yixuan/awtk/awtk/3rd/bgfx/bgfx/include -I/home/chen_yixuan/awtk/awtk/3rd/bgfx/bx/include -I/home/chen_yixuan/awtk/awtk/3rd/bgfx/bimg/include -I/home/chen_yixuan/awtk/awtk/3rd/agge -I/home/chen_yixuan/awtk/awtk/3rd/agg/include -I/home/chen_yixuan/awtk/awtk/3rd/nanovg -I/home/chen_yixuan/awtk/awtk/3rd/nanovg/gl -I/home/chen_yixuan/awtk/awtk/3rd/nanovg/base -I/home/chen_yixuan/awtk/awtk/3rd/nanovg/agge -I/home/chen_yixuan/awtk/awtk/3rd/nanovg/bgfx -I/home/chen_yixuan/awtk/awtk/3rd/SDL/src -I/home/chen_yixuan/awtk/awtk/3rd/SDL/include -I/home/chen_yixuan/awtk/awtk/3rd/agge/src -I/home/chen_yixuan/awtk/awtk/3rd/agge/include -I/home/chen_yixuan/awtk/awtk/3rd/gpinyin/include -I/home/chen_yixuan/awtk/awtk/3rd/libunibreak -I/home/chen_yixuan/awtk/awtk/3rd/gtest/googletest -I/home/chen_yixuan/awtk/awtk/3rd/gtest/googletest/include -I/home/chen_yixuan/awtk/awtk/tools -Isrc -Ires src/window_background.c
src/window_background.c: In function 'open_background_window':
src/window_background.c:132:11: warning: unused variable 'v' [-Wunused-variable]
  132 |   value_t v;
      |           ^
gcc -o src/window_basic.o -c -std=gnu99 -DLCD_WIDTH=800 -DLCD_HEIGHT=480 -DAPP_DEFAULT_FONT=\"default\" -DAPP_THEME=\"default\" -DAPP_RES_ROOT="\"../res\"" -DAPP_DEFAULT_LANGUAGE=\"en\" -DAPP_DEFAULT_COUNTRY=\"US\" -DAPP_ROOT="\"/home/chen_yixuan/awtk/awtk-examples/HelloDesigner-Demo\"" -g -Wall -Wno-unused-function -fPIC -DWITH_64BIT_CPU -DTK_ROOT="\"/home/chen_yixuan/awtk/awtk\"" -DWITH_MBEDTLS=1 -DENABLE_CURSOR=1 -DWITH_TEXT_BIDI=1 -DWITH_DATA_READER_WRITER=1 -DWITH_EVENT_RECORDER_PLAYER=1 -DWITH_ASSET_LOADER -DWITH_FS_RES -DWITH_ASSET_LOADER_ZIP -DSTBTT_STATIC -DSTB_IMAGE_STATIC -DWITH_STB_IMAGE -DWITH_VGCANVAS -DWITH_UNICODE_BREAK -DWITH_DESKTOP_STYLE -DWITH_SDL -DHAS_STDIO -DHAVE_STDIO_H -DHAS_GET_TIME_US64 -DHAS_STD_MALLOC -DTK_MAX_MEM_BLOCK_NR=3 -DWITH_IME_PINYIN -DWITH_NANOVG_GPU -DWITH_VGCANVAS_LCD -DWITH_STB_FONT -DWITH_NANOVG_GL3 -DWITH_NANOVG_GL -DLINUX -DHAS_PTHREAD -DSDL_REAL_API -DSDL_TIMER_UNIX -DSDL_VIDEO_DRIVER_X11 -DSDL_VIDEO_DRIVER_X11_SUPPORTS_GENERIC_EVENTS -DSDL_AUDIO_DRIVER_SNDIO -DSDL_VIDEO_OPENGL_GLX -DSDL_VIDEO_RENDER_OGL -DSDL_LOADSO_DLOPEN -DSDL_VIDEO_OPENGL_EGL -DSDL_VIDEO_OPENGL_ES2 -DSDL_REAL_API -DSDL_HAPTIC_DISABLED -DSDL_SENSOR_DISABLED -DSDL_JOYSTICK_DISABLED -DWITH_WIDGET_TYPE_CHECK=1 -DWITH_AWTK=1 -I/home/chen_yixuan/awtk/awtk -I/home/chen_yixuan/awtk/awtk/src -I/home/chen_yixuan/awtk/awtk/3rd -I/home/chen_yixuan/awtk/awtk/src/ext_widgets -I/home/chen_yixuan/awtk/awtk/src/custom_widgets -I/home/chen_yixuan/awtk/awtk/3rd/fribidi -I/home/chen_yixuan/awtk/awtk/3rd/mbedtls/include -I/home/chen_yixuan/awtk/awtk/3rd/mbedtls/3rdparty/everest/include -I/home/chen_yixuan/awtk/awtk/3rd/pixman -I/home/chen_yixuan/awtk/awtk/3rd/cairo -I/home/chen_yixuan/awtk/awtk/3rd/bgfx/bgfx/include -I/home/chen_yixuan/awtk/awtk/3rd/bgfx/bx/include -I/home/chen_yixuan/awtk/awtk/3rd/bgfx/bimg/include -I/home/chen_yixuan/awtk/awtk/3rd/agge -I/home/chen_yixuan/awtk/awtk/3rd/agg/include -I/home/chen_yixuan/awtk/awtk/3rd/nanovg -I/home/chen_yixuan/awtk/awtk/3rd/nanovg/gl -I/home/chen_yixuan/awtk/awtk/3rd/nanovg/base -I/home/chen_yixuan/awtk/awtk/3rd/nanovg/agge -I/home/chen_yixuan/awtk/awtk/3rd/nanovg/bgfx -I/home/chen_yixuan/awtk/awtk/3rd/SDL/src -I/home/chen_yixuan/awtk/awtk/3rd/SDL/include -I/home/chen_yixuan/awtk/awtk/3rd/agge/src -I/home/chen_yixuan/awtk/awtk/3rd/agge/include -I/home/chen_yixuan/awtk/awtk/3rd/gpinyin/include -I/home/chen_yixuan/awtk/awtk/3rd/libunibreak -I/home/chen_yixuan/awtk/awtk/3rd/gtest/googletest -I/home/chen_yixuan/awtk/awtk/3rd/gtest/googletest/include -I/home/chen_yixuan/awtk/awtk/tools -Isrc -Ires src/window_basic.c
gcc -o src/window_listview.o -c -std=gnu99 -DLCD_WIDTH=800 -DLCD_HEIGHT=480 -DAPP_DEFAULT_FONT=\"default\" -DAPP_THEME=\"default\" -DAPP_RES_ROOT="\"../res\"" -DAPP_DEFAULT_LANGUAGE=\"en\" -DAPP_DEFAULT_COUNTRY=\"US\" -DAPP_ROOT="\"/home/chen_yixuan/awtk/awtk-examples/HelloDesigner-Demo\"" -g -Wall -Wno-unused-function -fPIC -DWITH_64BIT_CPU -DTK_ROOT="\"/home/chen_yixuan/awtk/awtk\"" -DWITH_MBEDTLS=1 -DENABLE_CURSOR=1 -DWITH_TEXT_BIDI=1 -DWITH_DATA_READER_WRITER=1 -DWITH_EVENT_RECORDER_PLAYER=1 -DWITH_ASSET_LOADER -DWITH_FS_RES -DWITH_ASSET_LOADER_ZIP -DSTBTT_STATIC -DSTB_IMAGE_STATIC -DWITH_STB_IMAGE -DWITH_VGCANVAS -DWITH_UNICODE_BREAK -DWITH_DESKTOP_STYLE -DWITH_SDL -DHAS_STDIO -DHAVE_STDIO_H -DHAS_GET_TIME_US64 -DHAS_STD_MALLOC -DTK_MAX_MEM_BLOCK_NR=3 -DWITH_IME_PINYIN -DWITH_NANOVG_GPU -DWITH_VGCANVAS_LCD -DWITH_STB_FONT -DWITH_NANOVG_GL3 -DWITH_NANOVG_GL -DLINUX -DHAS_PTHREAD -DSDL_REAL_API -DSDL_TIMER_UNIX -DSDL_VIDEO_DRIVER_X11 -DSDL_VIDEO_DRIVER_X11_SUPPORTS_GENERIC_EVENTS -DSDL_AUDIO_DRIVER_SNDIO -DSDL_VIDEO_OPENGL_GLX -DSDL_VIDEO_RENDER_OGL -DSDL_LOADSO_DLOPEN -DSDL_VIDEO_OPENGL_EGL -DSDL_VIDEO_OPENGL_ES2 -DSDL_REAL_API -DSDL_HAPTIC_DISABLED -DSDL_SENSOR_DISABLED -DSDL_JOYSTICK_DISABLED -DWITH_WIDGET_TYPE_CHECK=1 -DWITH_AWTK=1 -I/home/chen_yixuan/awtk/awtk -I/home/chen_yixuan/awtk/awtk/src -I/home/chen_yixuan/awtk/awtk/3rd -I/home/chen_yixuan/awtk/awtk/src/ext_widgets -I/home/chen_yixuan/awtk/awtk/src/custom_widgets -I/home/chen_yixuan/awtk/awtk/3rd/fribidi -I/home/chen_yixuan/awtk/awtk/3rd/mbedtls/include -I/home/chen_yixuan/awtk/awtk/3rd/mbedtls/3rdparty/everest/include -I/home/chen_yixuan/awtk/awtk/3rd/pixman -I/home/chen_yixuan/awtk/awtk/3rd/cairo -I/home/chen_yixuan/awtk/awtk/3rd/bgfx/bgfx/include -I/home/chen_yixuan/awtk/awtk/3rd/bgfx/bx/include -I/home/chen_yixuan/awtk/awtk/3rd/bgfx/bimg/include -I/home/chen_yixuan/awtk/awtk/3rd/agge -I/home/chen_yixuan/awtk/awtk/3rd/agg/include -I/home/chen_yixuan/awtk/awtk/3rd/nanovg -I/home/chen_yixuan/awtk/awtk/3rd/nanovg/gl -I/home/chen_yixuan/awtk/awtk/3rd/nanovg/base -I/home/chen_yixuan/awtk/awtk/3rd/nanovg/agge -I/home/chen_yixuan/awtk/awtk/3rd/nanovg/bgfx -I/home/chen_yixuan/awtk/awtk/3rd/SDL/src -I/home/chen_yixuan/awtk/awtk/3rd/SDL/include -I/home/chen_yixuan/awtk/awtk/3rd/agge/src -I/home/chen_yixuan/awtk/awtk/3rd/agge/include -I/home/chen_yixuan/awtk/awtk/3rd/gpinyin/include -I/home/chen_yixuan/awtk/awtk/3rd/libunibreak -I/home/chen_yixuan/awtk/awtk/3rd/gtest/googletest -I/home/chen_yixuan/awtk/awtk/3rd/gtest/googletest/include -I/home/chen_yixuan/awtk/awtk/tools -Isrc -Ires src/window_listview.c
src/window_listview.c: In function 'open_listview_window':
src/window_listview.c:104:11: warning: unused variable 'v' [-Wunused-variable]
  104 |   value_t v;
      |           ^
gcc -o src/window_main.o -c -std=gnu99 -DLCD_WIDTH=800 -DLCD_HEIGHT=480 -DAPP_DEFAULT_FONT=\"default\" -DAPP_THEME=\"default\" -DAPP_RES_ROOT="\"../res\"" -DAPP_DEFAULT_LANGUAGE=\"en\" -DAPP_DEFAULT_COUNTRY=\"US\" -DAPP_ROOT="\"/home/chen_yixuan/awtk/awtk-examples/HelloDesigner-Demo\"" -g -Wall -Wno-unused-function -fPIC -DWITH_64BIT_CPU -DTK_ROOT="\"/home/chen_yixuan/awtk/awtk\"" -DWITH_MBEDTLS=1 -DENABLE_CURSOR=1 -DWITH_TEXT_BIDI=1 -DWITH_DATA_READER_WRITER=1 -DWITH_EVENT_RECORDER_PLAYER=1 -DWITH_ASSET_LOADER -DWITH_FS_RES -DWITH_ASSET_LOADER_ZIP -DSTBTT_STATIC -DSTB_IMAGE_STATIC -DWITH_STB_IMAGE -DWITH_VGCANVAS -DWITH_UNICODE_BREAK -DWITH_DESKTOP_STYLE -DWITH_SDL -DHAS_STDIO -DHAVE_STDIO_H -DHAS_GET_TIME_US64 -DHAS_STD_MALLOC -DTK_MAX_MEM_BLOCK_NR=3 -DWITH_IME_PINYIN -DWITH_NANOVG_GPU -DWITH_VGCANVAS_LCD -DWITH_STB_FONT -DWITH_NANOVG_GL3 -DWITH_NANOVG_GL -DLINUX -DHAS_PTHREAD -DSDL_REAL_API -DSDL_TIMER_UNIX -DSDL_VIDEO_DRIVER_X11 -DSDL_VIDEO_DRIVER_X11_SUPPORTS_GENERIC_EVENTS -DSDL_AUDIO_DRIVER_SNDIO -DSDL_VIDEO_OPENGL_GLX -DSDL_VIDEO_RENDER_OGL -DSDL_LOADSO_DLOPEN -DSDL_VIDEO_OPENGL_EGL -DSDL_VIDEO_OPENGL_ES2 -DSDL_REAL_API -DSDL_HAPTIC_DISABLED -DSDL_SENSOR_DISABLED -DSDL_JOYSTICK_DISABLED -DWITH_WIDGET_TYPE_CHECK=1 -DWITH_AWTK=1 -I/home/chen_yixuan/awtk/awtk -I/home/chen_yixuan/awtk/awtk/src -I/home/chen_yixuan/awtk/awtk/3rd -I/home/chen_yixuan/awtk/awtk/src/ext_widgets -I/home/chen_yixuan/awtk/awtk/src/custom_widgets -I/home/chen_yixuan/awtk/awtk/3rd/fribidi -I/home/chen_yixuan/awtk/awtk/3rd/mbedtls/include -I/home/chen_yixuan/awtk/awtk/3rd/mbedtls/3rdparty/everest/include -I/home/chen_yixuan/awtk/awtk/3rd/pixman -I/home/chen_yixuan/awtk/awtk/3rd/cairo -I/home/chen_yixuan/awtk/awtk/3rd/bgfx/bgfx/include -I/home/chen_yixuan/awtk/awtk/3rd/bgfx/bx/include -I/home/chen_yixuan/awtk/awtk/3rd/bgfx/bimg/include -I/home/chen_yixuan/awtk/awtk/3rd/agge -I/home/chen_yixuan/awtk/awtk/3rd/agg/include -I/home/chen_yixuan/awtk/awtk/3rd/nanovg -I/home/chen_yixuan/awtk/awtk/3rd/nanovg/gl -I/home/chen_yixuan/awtk/awtk/3rd/nanovg/base -I/home/chen_yixuan/awtk/awtk/3rd/nanovg/agge -I/home/chen_yixuan/awtk/awtk/3rd/nanovg/bgfx -I/home/chen_yixuan/awtk/awtk/3rd/SDL/src -I/home/chen_yixuan/awtk/awtk/3rd/SDL/include -I/home/chen_yixuan/awtk/awtk/3rd/agge/src -I/home/chen_yixuan/awtk/awtk/3rd/agge/include -I/home/chen_yixuan/awtk/awtk/3rd/gpinyin/include -I/home/chen_yixuan/awtk/awtk/3rd/libunibreak -I/home/chen_yixuan/awtk/awtk/3rd/gtest/googletest -I/home/chen_yixuan/awtk/awtk/3rd/gtest/googletest/include -I/home/chen_yixuan/awtk/awtk/tools -Isrc -Ires src/window_main.c
src/window_main.c: In function 'on_open_basic_window':
src/window_main.c:40:3: warning: implicit declaration of function 'open_basic_window'; did you mean 'on_open_basic_window'? [-Wimplicit-function-declaration]
   40 |   open_basic_window();
      |   ^~~~~~~~~~~~~~~~~
      |   on_open_basic_window
src/window_main.c: In function 'on_open_background_window':
src/window_main.c:48:3: warning: implicit declaration of function 'open_background_window'; did you mean 'on_open_background_window'? [-Wimplicit-function-declaration]
   48 |   open_background_window();
      |   ^~~~~~~~~~~~~~~~~~~~~~
      |   on_open_background_window
src/window_main.c: In function 'on_open_listview_window':
src/window_main.c:56:3: warning: implicit declaration of function 'open_listview_window'; did you mean 'on_open_listview_window'? [-Wimplicit-function-declaration]
   56 |   open_listview_window();
      |   ^~~~~~~~~~~~~~~~~~~~
      |   on_open_listview_window
src/window_main.c: In function 'on_open_animator_window':
src/window_main.c:65:3: warning: implicit declaration of function 'open_animator_window'; did you mean 'on_open_animator_window'? [-Wimplicit-function-declaration]
   65 |   open_animator_window();
      |   ^~~~~~~~~~~~~~~~~~~~
      |   on_open_animator_window
src/window_main.c: In function 'init_widget':
src/window_main.c:74:13: warning: unused variable 'win' [-Wunused-variable]
   74 |   widget_t* win = widget_get_window(widget);
      |             ^~~
gcc -o bin/demo -Wl,-rpath=./bin -Wl,-rpath=./ -Wl,-rpath=/home/chen_yixuan/awtk/awtk-examples/HelloDesigner-Demo/bin src/app_main.o src/window_animator.o src/window_background.o src/window_basic.o src/window_listview.o src/window_main.o -Llib -L/home/chen_yixuan/awtk/awtk/lib -L/home/chen_yixuan/awtk/awtk/bin -lawtk_global -lextwidgets -lwidgets -lbase -lgpinyin -lstreams -lconf_io -lhal -lcsv -lubjson -lcompressors -lfribidi -lmbedtls -lminiz -ltkc_static -llinebreak -lmbedtls -lnanovg -lSDL2 -lglad -lGL -lgtk-3 -lgdk-3 -lXext -lX11 -lsndio -lstdc++ -lasound -lpthread -lm -ldl
scons: done building targets.


```

SConscript

```bash
import os
import sys

env=DefaultEnvironment().Clone()
BIN_DIR=os.environ['BIN_DIR']

src_files = Glob('*.c')
src_files += Glob('custom_function/*.c')    
src_files += Glob('custom_widgets/*.c')
src_files += Glob('custom_widgets/*/*.c')

env.Program(os.path.join(BIN_DIR, 'demo'), src_files);
```

# awtk

修改字段E:\awtk\awtk-examples\HelloWorld.Xml-Demo\res\assets\default\raw\ui\main.xml

注意：在 AWTK 程序中是不会直接读取 XML 文件的，需要把 XML 文件转换到 bin 文件才可以被 AWTK 程序读取，所以换句话来说，我们需要编写 XML 文件，然后通过 AWTK 提供的工具把 XML 文件转换到 bin 文件。

```cmd
xml_to_ui.exe D:\AWTK\SDK\user_apps\AwtkApplication\design\default\ui\home_page.xml D:\AWTK\SDK\user_apps\AwtkApplication\design\default\ui\home_page.bin [bin]
```

![image-20210804135242308](https://gitee.com/ling66611/picgo-image/raw/master/master/image-20210804135242308.png)