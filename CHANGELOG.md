vcpkg (0.0.81)
--------------
  * Add ports:
    - atlmfc               0
    - giflib               5.1.4
    - graphicsmagick       1.3.25
    - libmad               0.15.1
    - libsndfile           libsndfile-1.0.29-6830c42
    - ms-gsl               20170425-8b320e3f5d016f953e55dfc7ec8694c1349d3fe4 (**see below)
    - taglib               1.11.1-1
    - xalan-c              1.11-1
  * Update ports:
    - ace                  6.4.2 -> 6.4.3
    - bond                 5.2.0 -> 5.3.1
    - boost                1.63-4 -> 1.64-2
    - cppzmq               0.0.0-1 -> 4.2.1
    - gdal                 1.11.3-1 -> 1.11.3-3
    - gdk-pixbuf           2.36.5 -> 2.36.6
    - grpc                 1.1.2-1 -> 1.2.3
    - gsl                  0-fd5ad87bf -> 2.3 (**see below)
    - harfbuzz             1.3.4-2 -> 1.4.6
    - icu                  58.2-1 -> 59.1-1
    - libflac              1.3.2-1 -> 1.3.2-2
    - libmodplug           0.8.8.5-bb25b05 -> 0.8.9.0
    - pango                1.40.4 -> 1.40.5-1
    - pcre                 8.38-1 -> 8.40
    - poco                 1.7.6-4 -> 1.7.8
    - qt5                  5.7.1-7 -> 5.8-1
    - wt                   3.3.6-3 -> 3.3.7
  * The Guidelines Support Library has been renamed from`gsl` to `ms-gsl`. The GNU Scientific Library has been added as `gsl`.
  * Introducing `vcpkg export` command:
    - Exports one or more installed packages along with their dependencies
    - Options for target format: --nuget --7zip --zip --raw (can specify more than one)
    - Option `--dry-run`: This will print out the export plan, but will not actually perform the export
    - More information and examples [here](https://blogs.msdn.microsoft.com/vcblog/2017/05/03/vcpkg-introducing-export-command/).
  * Add `--head` option for `vcpkg install`. It only applies to github-based project and allows you to use the latest master commit
    - For example: `./vcpkg install cpprestsdk:x64-windows --head` will build cpprestsdk from the latest master commit instead of version 2.9.0 specified in the `CONTROL` file
  * Bump auto-downloaded version of `cmake` to 3.8.0 (was 3.8.0rc1)
  * `--options` are now case-insensitive
  * `vcpkg` now uses `clang-format`
  * Fixes and improvements in the `vcpkg` tool

-- vcpkg team <vcpkg@microsoft.com>  WED, 03 May 2017 18:00:00 -0800


vcpkg (0.0.80)
--------------
  * Add ports:
    - clapack              3.2.1
    - geographiclib        1.47-patch1-3
    - libevent             2.1.8-1
    - mdnsresponder        765.30.11
    - openblas             v0.2.19-1
    - picojson             1.3.0
    - sdl2-mixer           2.0.1
    - sdl2-net             2.0.1
    - sdl2-ttf             2.0.14
  * Update ports:
    - azure-storage-cpp    3.0.0 -> 3.0.0-2
    - catch                1.8.2 -> 1.9.1
    - eigen3               3.3.0 -> 3.3.3
    - glib                 2.50.3 -> 2.52.1
    - libbson              1.5.1 -> 1.6.2
    - libpng               1.6.28 -> 1.6.28-1
    - libvorbis            1.3.5-1-143caf4023a90c09a5eb685fdd46fb9b9c36b1ee -> 1.3.5-143caf4-2
    - libxml2              2.9.4 -> 2.9.4-1
    - mongo-c-driver       1.5.1 -> 1.6.2
    - mongo-cxx-driver     3.0.3-1 -> 3.1.1
    - opencv               3.2.0 -> 3.2.0-1
    - qwt                  6.1.3 -> 6.1.3-1
    - uwebsockets          0.14.1 -> 0.14.2
    - xerces-c             3.1.4 -> 3.1.4-3
  * Added `System32\Wbem` to the sanizited environment
  * `--debug` flag will now show environment information when launching external commands
  * `vcpkg install` command has been enhanced:
    - When a package build starts or ends, a message with the package name is diplayed
    - Before the start of the build, a summary of the install plan is displayed
    - Added new option `--dry-run`: This will print out the install plan, but will not actually perform the install
  * Add CI badge in the front page
  * Fix WindowsSDK detection to correctly handle the new optional c++ desktop deployment of the Windows SDK.
  * Reduce verbosity of `vcpkg remove` when purging the package
  * Fixes and improvements in the `vcpkg` tool itself

-- vcpkg team <vcpkg@microsoft.com>  WED, 18 Apr 2017 18:00:00 -0800


vcpkg (0.0.79)
--------------
  * Add ports:
    - ecm                  5.32.0
    - libgd                2.2.4-1
    - octomap              cefed0c1d79afafa5aeb05273cf1246b093b771c-1
  * Update ports:
    - boost                1.63-3 -> 1.63-4
    - cuda                 8.0 -> 8.0-1
    - freeimage            3.17.0 -> 3.17.0-1
    - freetype             2.6.3-4 -> 2.6.3-5
    - glfw3                3.2.1 -> 3.2.1-1
    - libarchive           3.2.2-2 -> 3.3.1
    - pqp                  1.3 -> 1.3-1
    - qt5                  5.7.1-6 -> 5.7.1-7
    - sqlite3              3.17.0 -> 3.18.0-1
  * `vcpkg` has exceeded 200 libraries!
  * `vcpkg remove` command has been reworked:
    - `vcpkg remove <pkg>` now uninstalls and deletes the package by default. Previously, this was the behavior of `vpckg remove --purge <pkg>`
    - `vcpkg remove <pkg> --no-purge` now uninstalls the package without deleting it. Previously, this was the behavior or `vcpkg remove <pkg>`
    - Added new option `--dry-run`: This will print out the remove plan, but will not actually perform the removal
    - Added new option `--outdated`: Using `vcpkg remove --outdated` will remove all packages for which updates are available
  * Add `bootstrap-vcpkg.bat` in the root directory for easier building of `vcpkg`
    - Also fix a regression with `vcpkg` bootstrapping
  * Add information about how to use header-only libraries from cmake in [EXAMPLES.md](docs\EXAMPLES.md)
  * `vcpkg build_external` changed to `vcpkg build-external` (underscore to dash)
  * Fixes and improvements in existing portfiles and the `vcpkg` tool itself

-- vcpkg team <vcpkg@microsoft.com>  WED, 05 Apr 2017 15:00:00 -0800


vcpkg (0.0.78)
--------------
  * Add ports:
    - libp7-baical         4.1
    - pybind11             2.1.0
    - xxhash               0.6.2
  * Update ports:
    - catch                1.8.1            -> 1.8.2
    - glog                 0.3.4-0472b91    -> 0.3.4-0472b91-1
    - libuv                1.10.1           -> 1.10.1-2
    - libwebp              0.5.1-1          -> 0.6.0-1
    - range-v3             20150729-vcpkg2  -> 20150729-vcpkg3
    - tiff                 4.0.6-2          -> 4.0.7
    - uwebsockets          0.13.0-1         -> 0.14.1
  * `--debug` flag enhanced to give line information on any exit. Applies to any `vcpkg` command
  * Improve error messages when requesting a portfile that does not exist (for example via command line or via dependencies)
  * Add `EMPTY_INCLUDE_FOLDER` policy
  * Fixes and improvements in existing portfiles and the `vcpkg` tool itself

-- vcpkg team <vcpkg@microsoft.com>  TUE, 28 Mar 2017 21:15:00 -0800


vcpkg (0.0.77)
--------------
  * Add ports:
    - beast                1.0.0-b30
    - botan                2.0.1
    - cairomm              1.15.3-1
    - dlfcn-win32          1.1.0
    - freerdp              2.0.0-beta1+android11
    - gdcm2                2.6.7
    - jbigkit              2.1
    - libpopt              1.16-10~vcpkg1
    - libvpx               1.6.1-1
    - libwebm              1.0.0.27-1
    - msgpack              2.1.1
    - nlohmann-json        2.1.1
    - pcre2                10.23
    - tinyexr              v0.9.5-d16ea6
    - xlnt                 0.9.4
  * Update ports:
    - antlr4               4.6              -> 4.6-1
    - atk                  2.22.0           -> 2.24.0
    - boost                1.63-2           -> 1.63-3
    - dlib                 19.2             -> 19.4-1
    - glib                 2.50.2           -> 2.50.3
    - gtk                  3.22.8           -> 3.22.11
    - libepoxy             1.4.0-2432daf-1  -> 1.4.1-7d58fd3
    - libjpeg-turbo        1.4.90-1         -> 1.5.1-1
    - liblzma              5.2.3            -> 5.2.3-1
    - mpg123               1.23.3           -> 1.24.0-1
    - mpir                 2.7.2-1          -> 3.0.0-2
    - pango                1.40.3           -> 1.40.4
    - qt5                  5.7.1-5          -> 5.7.1-6
    - uwebsockets          0.12.0           -> 0.13.0-1
  * Improvements and fixes in the sanizited environment introduced in the previous version
  * `--debug` flag now gives line information when an error occurs. Applies to any `vcpkg` command
  * Fixes and improvements around launching powershell scripts
    - Correct handling of spaces in the path
    - Ignore user profile (-NoProfile)
  * `openssl`: Enable building in paths with space and ignore installed versions in `C:/OpenSSL/`
  * Fixes and improvements in existing portfiles and the `vcpkg` tool itself

-- vcpkg team <vcpkg@microsoft.com>  WED, 22 Mar 2017 15:30:00 -0800


vcpkg (0.0.76)
--------------
  * Add ports:
    - ffmpeg               3.2.4-2
    - fftw3                3.3.6-p11
    - flatbuffers          1.6.0
    - netcdf-c             4.4.1.1-1
    - netcdf-cxx4          4.3.0
    - portaudio            19.0.6.00
    - vtk                  7.1.0
  * Update ports:
    - azure-storage-cpp    2.6.0            -> 3.0.0
    - boost                1.63             -> 1.63-2
    - bullet3              2.83.7.98d4780   -> 2.86.1
    - catch                1.5.7            -> 1.8.1
    - cppwinrt             1.010.0.14393.0  -> feb2017_refresh-14393
    - hdf5                 1.8.18           -> 1.10.0-patch1-1
    - libflac              1.3.2            -> 1.3.2-1
    - libpng               1.6.24-1         -> 1.6.28
    - lua                  5.3.3-2          -> 5.3.4
    - msmpi                8.0              -> 8.0-1
    - openjpeg             2.1.2            -> 2.1.2-1
    - poco                 1.7.6-3          -> 1.7.6-4
    - szip                 2.1              -> 2.1-1
    - zeromq               4.2.0            -> 4.2.2
  * `vcpkg` now launches external commands (most notably builds) in a sanitized environment
  * Better proxy handling when fetching dependencies (cmake/git/nuget)
  * Fix more VS2017 issues
  * Fixes and improvements in existing portfiles and the `vcpkg` tool itself

-- vcpkg team <vcpkg@microsoft.com>  MON, 10 Mar 2017 17:45:00 -0800


vcpkg (0.0.75)
--------------
  * Add ports:
    - dlib                 19.2
    - gtk                  3.22.8
    - pqp                  1.3
    - pugixml              1.8.1
  * Update ports:
    - clockutils           1.1.1            -> 1.1.1-3651f232c27074c4ceead169e223edf5f00247c5
    - grpc                 1.1.0-dev-1674f65-2 -> 1.1.2-1
    - libflac              1.3.1-1          -> 1.3.2
    - liblzma              5.2.2            -> 5.2.3
    - libmysql             5.7.17           -> 5.7.17-1
    - lz4                  1.7.4.2          -> 1.7.5
    - mongo-cxx-driver     3.0.3            -> 3.0.3-1
    - nana                 1.4.1            -> 1.4.1-66be23c9204c5567d1c51e6f57ba23bffa517a7c
    - opengl               10.0.10240.0     -> 0.0-3
    - protobuf             3.0.2            -> 3.2.0
    - qt5                  5.7.1-2          -> 5.7.1-5
    - spdlog               0.11.0           -> 0.12.0
  * Numerous improvements in Visual Studio, MSBuild and Windows SDK auto-detection
  * `vcpkg integrate install` now outputs the specific toolchain file to use for CMake integration
  * All commands now checks for `--options` and will issue an error on unknown options.
    - Previously only commands with options would do this (for example `vcpkg remove --purge <pkg>`) and commands with no options would ignore them, for example `vcpkg install --purge <pkg>`
  * Update version of the automatically acquired JOM, python
    - Also, for python: automatically acquire the 32-bit versions instead of the 64-bit ones
  * Fixes and improvements in existing portfiles and the `vcpkg` tool itself

-- vcpkg team <vcpkg@microsoft.com>  MON, 27 Feb 2017 14:00:00 -0800


vcpkg (0.0.74)
--------------
  * Bump required version & auto-downloaded version of `cmake` to 3.8.0 (was 3.7.x). This fixes UWP builds with Visual Studio 2017
  * Fix `vcpkg build` not printing out the missing dependencies on fail
  * Fixes and improvements in the `vcpkg` tool itself

-- vcpkg team <vcpkg@microsoft.com>  THU, 16 Feb 2017 18:15:00 -0800


vcpkg (0.0.73)
--------------
  * Add ports:
    - gdk-pixbuf           2.36.5
    - openvr               1.0.5
  * Update ports:
    - lmdb                 0.9.18-1         -> 0.9.18-2
    - opencv               3.1.0-1          -> 3.2.0
    - sqlite3              3.15.0           -> 3.17.0
  * Add functions to correctly find the "Program Files" folders in all parts of `vcpkg` (C++, CMake, powershell)
  * Flush std::cout before launching an external process. Fixes issues when redirecting std::cout to a file
  * Update version of the automatically acquired nasm. Resolves build failure with libjpeg-turbo
  * Change the format of the listfile. The file is now sorted and directories now have a trailing slash so they can easily be identified.
     - Old listfiles will be automatically updated on first access. This will happen to all old listfiles when a new package is installed (`vcpkg install`) or after a call to `vcpkg owns`.
  * Fixes and improvements in existing portfiles and the `vcpkg` tool itself

-- vcpkg team <vcpkg@microsoft.com>  WED, 15 Feb 2017 19:30:00 -0800


vcpkg (0.0.72)
--------------
  * Add ports:
    - cuda                 8.0
    - hdf5                 1.8.18
    - lcms                 2.8
    - libepoxy             1.4.0-2432daf-1
    - libnice              0.1.13
    - msmpi                8.0
    - parmetis             4.0.3
    - sqlite-modern-cpp    2.4
    - websocketpp          0.7.0
  * Update ports:
    - asio                 1.10.6           -> 1.10.8
    - aws-sdk-cpp          1.0.47           -> 1.0.61
    - bond                 5.0.0-4-g53ea136 -> 5.2.0
    - cpprestsdk           2.9.0-1          -> 2.9.0-2
    - fmt                  3.0.1-1          -> 3.0.1-4
    - grpc                 1.1.0-dev-1674f65-1 -> 1.1.0-dev-1674f65-2
    - libraw               0.17.2-2         -> 0.18.0-1
    - libvorbis            1.3.5-143caf4023a90c09a5eb685fdd46fb9b9c36b1ee -> 1.3.5-1-143caf4023a90c09a5eb685fdd46fb9b9c36b1ee
    - poco                 1.7.6-2          -> 1.7.6-3
    - rapidjson            1.0.2-1          -> 1.1.0
    - sfml                 2.4.1            -> 2.4.2
    - wt                   3.3.6-2          -> 3.3.6-3
  * Introduce Build Policies:
     - Packages with special characteristics (e.g. CUDA) can now use Build Policies to control which post-build checks apply to them.
  * Improve support for Visual Studio 2017
    - Add auto-detection for Windows SDK
    - Fixed various issues with `bootstrap.ps1` and VS2017 support
  * Automatic acquisition of perl now uses the 32-bit version isntead of the 64-bit version
  * Fix `vcpkg remove --purge` not applying to non-installed packages
  * Fixes and improvements in existing portfiles and the `vcpkg` tool itself

-- vcpkg team <vcpkg@microsoft.com>  TUE, 14 Feb 2017 11:30:00 -0800


vcpkg (0.0.71)
--------------
  * Add ports:
    - atk                  2.22.0
    - fontconfig           2.12.1
    - opus                 1.1.4
    - pango                1.40.3
    - xerces-c             3.1.4
  * Update ports:
    - boost                1.62-11          -> 1.63
    - cairo                1.14.6           -> 1.15.4
    - directxtk            dec2016          -> dec2016-1
    - fltk                 1.3.4-1          -> 1.3.4-2
    - gdal                 1.11.3           -> 1.11.3-1
    - harfbuzz             1.3.4            -> 1.3.4-2
    - libarchive           3.2.2            -> 3.2.2-2
    - libmariadb           2.3.1            -> 2.3.2
    - mpir                 2.7.2            -> 2.7.2-1
    - openssl              1.0.2j-2         -> 1.0.2k-2
    - wt                   3.3.6            -> 3.3.6-2
  * Improve `vcpkg remove`:
     - Now shows all dependencies that need to be removed instead of just the immediate dependencies
     - Add `--recurse` option that removes all dependencies
     - Improve messages
  * Improve support for Visual Studio 2017
    - Better VS2017 detection
    - Fixed various issues with `bootstrap.ps1` and VS2017 support
  * Fix `vcpkg_copy_pdbs()` under non-English locale
  * Notable changes for buiding the `vcpkg` tool:
    - Restructure `vcpkg` project hierarchy. Now only has 4 projects (down from 6). Most of the code now lives under vcpkglib.vcxproj
    - Enable multiprocessor compilation
    - Disable MinimalRebuild
    - Use precompiled headers
  * Fixes and improvements in existing portfiles and the `vcpkg` tool itself

-- vcpkg team <vcpkg@microsoft.com>  MON, 30 Jan 2017 23:00:00 -0800


vcpkg (0.0.70)
--------------
  * Add ports:
    - fltk                 1.3.4-1
    - glib                 2.50.2
    - lzo                  2.09
    - uvatlas              sept2016
  * Update ports:
    - dx                   1.0.0            -> 1.0.1
    - libmysql             5.7.16           -> 5.7.17
  * Add support for Visual Studio 2017
    - Previously, you could use Visual Studio 2017 for your own application and `vcpkg` integration would work, but you needed to have Visual Studio 2015 to build `vcpkg` itself as well as the libraries. This requirement has now been removed
    - If both Visual Studio 2015 and Visual Studio 2017 are installed, Visual Studio 2017 tools will be preferred over those of Visual Studio 2015
  * Bump required version & auto-downloaded version of `cmake` to 3.7.2 (was 3.5.x), which includes generators for Visual Studio 2017
  * Bump auto-downloaded version of `nuget` to 3.5.0 (was 3.4.3)
  * Bump auto-downloaded version of `git` to 2.11.0 (was 2.8.3)
  * Fixes and improvements in existing portfiles and the `vcpkg` tool itself

-- vcpkg team <vcpkg@microsoft.com>  MON, 23 Jan 2017 19:50:00 -0800


vcpkg (0.0.67)
--------------
  * Add ports:
    - cereal               1.2.1
    - directxmesh          oct2016
    - directxtex           dec2016
    - metis                5.1.0
    - sdl2-image           2.0.1
    - szip                 2.1
  * Update ports:
    - ace                  6.4.0            -> 6.4.2
    - boost                1.62-9           -> 1.62-11
    - curl                 7.51.0-2         -> 7.51.0-3
    - directxtk            oct2016-1        -> dec2016
    - directxtk12          oct2016          -> dec2016
    - freetype             2.6.3-3          -> 2.6.3-4
    - glew                 2.0.0            -> 2.0.0-1
    - grpc                 1.1.0-dev-1674f65 -> 1.1.0-dev-1674f65-1
    - http-parser          2.7.1            -> 2.7.1-1
    - libssh2              1.8.0            -> 1.8.0-1
    - libwebsockets        2.0.0            -> 2.0.0-1
    - openssl              1.0.2j-1         -> 1.0.2j-2
    - tiff                 4.0.6-1          -> 4.0.6-2
    - zlib                 1.2.10           -> 1.2.11
  * Add 7z to `vcpkg_find_acquire_program.cmake`
  * Enhance `vcpkg_build_cmake.cmake` and `vcpkg_install_cmake.cmake`:
    - Add option to disable parallel building (it is enabled by default)
    - Add option to use the 64-bit toolset (for the 32-bit builds; output binaries are still 32-bit)
  * Fix bug in `applocal.ps1` that would infinitely recurse when there were no depenndencies
  * Fixes and improvements in existing portfiles and the `vcpkg` tool itself

-- vcpkg team <vcpkg@microsoft.com>  WED, 18 Jan 2017 13:45:00 -0800


vcpkg (0.0.66)
--------------
  * Add ports:
    - antlr4               4.6
    - bzip2                1.0.6
    - dx                   1.0.0
    - gli                  0.8.2
    - libarchive           3.2.2
    - libffi               3.1
    - liblzma              5.2.2
    - libmodplug           0.8.8.5-bb25b05
    - libsigcpp            2.10
    - lmdb                 0.9.18-1
    - lz4                  1.7.4.2
    - ogre                 1.9.0
    - qwt                  6.1.3
    - smpeg2               2.0.0
    - spirv-tools          1.1-f72189c249ba143c6a89a4cf1e7d53337b2ddd40
  * Update ports:
    - aws-sdk-cpp          1.0.34-1         -> 1.0.47
    - azure-storage-cpp    2.5.0            -> 2.6.0
    - boost                1.62-8           -> 1.62-9
    - chakracore           1.3.1            -> 1.4.0
    - freetype             2.6.3-2          -> 2.6.3-3
    - icu                  58.1             -> 58.2-1
    - libbson              1.5.0-rc6        -> 1.5.1
    - libvorbis                             -> 1.3.5-143caf4023a90c09a5eb685fdd46fb9b9c36b1ee
    - lua                  5.3.3-1          -> 5.3.3-2
    - mongo-c-driver       1.5.0-rc6        -> 1.5.1
    - pixman               0.34.0           -> 0.34.0-1
    - qt5                  5.7-1            -> 5.7.1-2
    - sdl2                 2.0.5            -> 2.0.5-2
    - zlib                 1.2.8            -> 1.2.10
  * Improvements in pre-install checks:
    - Refactor file-exists-check. Improved clarity and performance.
  * Fixes and improvements in existing portfiles and the `vcpkg` tool itself

-- vcpkg team <vcpkg@microsoft.com>  TUE, 10 Jan 2017 17:15:00 -0800


vcpkg (0.0.65)
--------------
  * Add ports:
    - anax                 2.1.0-1
    - aws-sdk-cpp          1.0.34-1
    - azure-storage-cpp    2.5.0
    - charls               2.0.0
    - dimcli               1.0.3
    - entityx              1.2.0
    - freeimage            3.17.0
    - gdal                 1.11.3
    - globjects            1.0.0
    - http-parser          2.7.1
    - icu                  58.1
    - libflac              1.3.1-1
    - libssh2              1.8.0
    - nana                 1.4.1
    - qca                  2.2.0
    - sfml                 2.4.1
    - shaderc              2df47b51d83ad83cbc2e7f8ff2b56776293e8958
    - uwebsockets          0.12.0
    - yaml-cpp             0.5.4 candidate
  * Update ports:
    - boost                1.62-6           -> 1.62-8
    - curl                 7.51.0-1         -> 7.51.0-2
    - gflags               2.1.2            -> 2.2.0-2
    - glbinding            2.1.1            -> 2.1.1-1
    - glslang              1c573fbcfba6b3d631008b1babc838501ca925d3 -> 1c573fbcfba6b3d631008b1babc838501ca925d3-1
    - harfbuzz             1.3.2            -> 1.3.4
    - jxrlib               1.1-1            -> 1.1-2
    - libraw               0.17.2           -> 0.17.2-2
    - lua                  5.3.3            -> 5.3.3-1
    - openssl              1.0.2j           -> 1.0.2j-1
  * Improvements in the post-build checks:
    - Add check for files in the `<package>\` dir and `<package>\debug\` dir
  * Introduce pre-install checks:
    - The `install` command now checks that files will not be overwrriten when installing a package. A particular file can only be owned by a single package
  * Introduce 'lib\manul-link\' directory. Libraries placing the lib files in that directory are not automatically added to the link line
  * Disable all interactions with CMake registry
  * `vcpkg /?` is now a valid equivalent of `vcpkg help`
  * Fixes and improvements in existing portfiles and the `vcpkg` tool itself

-- vcpkg team <vcpkg@microsoft.com>  MON, 12 Dec 2016 18:15:00 -0800


vcpkg (0.0.61)
--------------
  * Add ports:
    - cairo                1.14.6
    - clockutils           1.1.1
    - directxtk            oct2016-1
    - directxtk12          oct2016
    - glslang              1c573fbcfba6b3d631008b1babc838501ca925d3
    - libodb-pgsql         2.4.0
    - pixman               0.34.0
    - proj                 4.9.3
    - zstd                 1.1.1
  * Update ports:
    - chakracore           1.3.0            -> 1.3.1
    - curl                 7.51.0           -> 7.51.0-1
    - dxut                 11.14            -> 11.14-2
    - fmt                  3.0.1            -> 3.0.1-1
    - freetype             2.6.3-1          -> 2.6.3-2
    - rxcpp                2.3.0            -> 3.0.0
    - think-cell-range     1d785d9          -> e2d3018
    - tiff                 4.0.6            -> 4.0.6-1
  * Fixes and improvements in existing portfiles and the `vcpkg` tool itself

-- vcpkg team <vcpkg@microsoft.com>  MON, 28 Nov 2016 18:30:00 -0800


vcpkg (0.0.60)
--------------
  * Add ports:
    - box2d                2.3.1-374664b
    - decimal-for-cpp      1.12
    - jsoncpp              1.7.7
    - libpq                9.6.1
    - libxslt              1.1.29
    - poco                 1.7.6-2
    - qt5                  5.7-1
    - signalrclient        1.0.0-beta1
    - soci                 2016.10.22
    - tclap                1.2.1
  * Update ports:
    - boost                1.62-1           -> 1.62-6
    - chakracore           1.2.0.0          -> 1.3.0
    - eigen3               3.2.10-2         -> 3.3.0
    - fmt                  3.0.0-1          -> 3.0.1
    - jxrlib               1.1              -> 1.1-1
    - libbson              1.4.2            -> 1.5.0-rc6
    - libuv                1.9.1            -> 1.10.1
    - libwebp              0.5.1            -> 0.5.1-1
    - mongo-c-driver       1.4.2            -> 1.5.0-rc6
    - mongo-cxx-driver     3.0.2            -> 3.0.3
    - pcre                 8.38             -> 8.38-1
    - sdl2                 2.0.4            -> 2.0.5
  * `vcpkg` has exceeded 100 libraries!
  * Rework dependency handling
  * Many more portfiles now support static builds. The remaining ones warn that static is not yet supported and will perform a dynamic build instead
  * The triplet file is now automatically included and is available in every portfile
  * Improvements in the post-build checks:
    - Introduce `BUILD_INFO` file. This contains information about the settings used in the build. The post-build checks use this file to choose what checks to perform
    - Add CRT checks
    - Improve coff file reader. It is now more robust and it correctly handles a couple of corner cases
    - A few miscellaneous checks to further prevent potential issues with the produced packages
  * Improve integration and fix related issues
  * Add support for VS 2017
  * Introduce function that tries to repeatedly build up to a number of failures. This reduces/resolves issues from libraries with flaky builds
  * Many fixes and improvements in existing portfiles and the `vcpkg` tool itself

-- vcpkg team <vcpkg@microsoft.com>  WED, 23 Nov 2016 15:30:00 -0800


vcpkg (0.0.51)
--------------
  * Add simple substring search to `vcpkg cache`
  * Add simple substring search to `vcpkg list`

-- vcpkg team <vcpkg@microsoft.com>  MON, 07 Nov 2016 14:45:00 -0800


vcpkg (0.0.50)
--------------
  * Add ports:
    - apr                  1.5.2
    - assimp               3.3.1
    - boost-di             1.0.1
    - bullet3              2.83.7.98d4780
    - catch                1.5.7
    - chakracore           1.2.0.0
    - cppwinrt             1.010.0.14393.0
    - cppzmq               0.0.0-1
    - cryptopp             5.6.5
    - double-conversion    2.0.1
    - dxut                 11.14
    - fastlz               1.0
    - freeglut             3.0.0
    - geos                 3.5.0
    - gettext              0.19
    - glbinding            2.1.1
    - glog                 0.3.4-0472b91
    - harfbuzz             1.3.2
    - jxrlib               1.1
    - libbson              1.4.2
    - libccd               2.0.0
    - libmariadb           2.3.1
    - libmysql             5.7.16
    - libodb               2.4.0
    - libodb-sqlite        2.4.0
    - libogg               1.3.2
    - libraw               0.17.2
    - libtheora            1.1.1
    - libvorbis
    - libwebp              0.5.1
    - libxml2              2.9.4
    - log4cplus            1.1.3-RC7
    - lua                  5.3.3
    - mongo-c-driver       1.4.2
    - mongo-cxx-driver     3.0.2
    - nanodbc              2.12.4
    - openjpeg             2.1.2
    - pcre                 8.38
    - pdcurses             3.4
    - physfs               2.0.3
    - rxcpp                2.3.0
    - spdlog               0.11.0
    - tbb                  20160916
    - think-cell-range     1d785d9
    - utfcpp               2.3.4
    - wt                   3.3.6
    - wtl                  9.1
    - zeromq               4.2.0
    - zziplib              0.13.62
  * Update ports:
    - boost                1.62             -> 1.62-1
    - cpprestsdk           2.8              -> 2.9.0-1
    - curl                 7.48.0           -> 7.51.0
    - eigen3               3.2.9            -> 3.2.10-2
    - freetype             2.6.3            -> 2.6.3-1
    - glew                 1.13.0           -> 2.0.0
    - openssl              1.0.2h           -> 1.0.2j
    - range-v3             0.0.0-1          -> 20150729-vcpkg2
    - sqlite3              3120200          -> 3.15.0
  * Add support for static libraries
  * Add more post build checks
  * Improve post build checks related to verifying information in the dll/pdb files (e.g. architecture)
  * Many fixes in existing portfiles
  * Various updates in FAQ
  * Release builds now create pdbs (debug builds already did)

-- vcpkg team <vcpkg@microsoft.com>  MON, 07 Nov 2016 00:01:00 -0800


vcpkg (0.0.40)
--------------
  * Add ports:
    - ace 6.4.0
    - asio 1.10.6
    - bond 5.0.0
    - constexpr 1.0
    - doctest 1.1.0
    - eigen3 3.2.9
    - fmt 3.0.0
    - gflags 2.1.2
    - glm 0.9.8.1
    - grpc 1.1.0
    - gsl 0-fd5ad87bf
    - gtest 1.8
    - libiconv 1.14
    - mpir 2.7.2
    - protobuf 3.0.2
    - ragel 6.9
    - rapidxml 1.13
    - sery 1.0.0
    - stb 1.0
  * Update ports:
    - boost 1.62
    - glfw3 3.2.1
    - opencv 3.1.0-1
  * Various fixes in existing portfiles
  * Introduce environment variable `VCPKG_DEFAULT_TRIPLET`
  * Replace everything concerning MD5 with SHA512
  * Add mirror support
  * `vcpkg` now checks for valid package names: only ASCII lowercase chars, digits, or dashes are allowed
  * `vcpkg create` now also creates a templated CONTROL file
  * `vcpkg create` now checks for invalid chars in the zip path
  * `vcpkg edit` now throws an error if it cannot launch an editor
  * Fix `vcpkg integrate` to only apply to C++ projects instead of all projects
  * Fix `vcpkg integrate` locale-specific failures
  * `vcpkg search` now does simple substring searching
  * Fix path that assumed Visual Studio is installed in default location
  * Enable multicore builds by default
  * Add `.vcpkg-root` file to detect the root directory
  * Fix `bootstrap.ps1` to work with older versions of powershell
  * Add `SOURCE_PATH` variable to all portfiles.
  * Many improvements in error messages shown by `vcpkg`
  * Various updates in FAQ
  * Move `CONTRIBUTING.md` to root

-- vcpkg team <vcpkg@microsoft.com>  WED, 05 Oct 2016 17:00:00 -0700


vcpkg (0.0.30)
--------------
  * DLLs are now accompanied with their corresponding PDBs.
  * Rework removal commands. `vcpkg remove <pkg>` now uninstalls the package. `vcpkg remove --purge <pkg>` now uninstalls and also deletes the package.
  * Rename option --arch to --triplet.
  * Extensively rework directory tree layout to make it more intuitive.
  * Improve post-build verification checks.
  * Improve post-build verification messages; they are now more compact, more consistent and contain more suggestions on how to resolve the issues found.
  * Fix `vcpkg integrate project` in cases where the path contained non-alphanumeric chars.
  * Improve handling of paths. In general, commands with whitespace and non-ascii characters should be handled better now.
  * Add colorized output for `vcpkg clean` and `vcpkg purge`.
  * Add colorized output for many more errors.
  * Improved `vcpkg update` to identify installed libraries that are out of sync with their portfiles.
  * Added list of example port files to EXAMPLES.md
  * Rename common CMake utilities to use prefix `vcpkg_`.
  * [libpng] Fixed x86-uwp and x64-uwp builds.
  * [libjpeg-turbo] Fixed x86-uwp and x64-uwp builds via suppressing static CRT linkage.
  * [rapidjson] New library.

-- vcpkg team <vcpkg@microsoft.com>  WED, 18 Sep 2016 20:50:00 -0700
