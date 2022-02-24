additional_target_cpus
Current value (from the default) = []
From //build/config/ios/ios_sdk.gni:58

    If non-empty, this list must contain valid cpu architecture, and the final
    build will be a multi-architecture build (aka fat build) supporting the
    main $target_cpu architecture and all of $additional_target_cpus.

    For example to build an application that will run on both arm64 and armv7
    devices, you would use the following in args.gn file when running "gn args":

      target_os = "ios"
      target_cpu = "arm64"
      additional_target_cpus = [ "arm" ]

    You can also pass the value via "--args" parameter for "gn gen" command by
    using the syntax --args='additional_target_cpus=["arm"] target_cpu="arm64"'.

aec_untrusted_delay_for_testing
Current value (from the default) = false
From //webrtc/modules/audio_processing/BUILD.gn:17

    Disables the usual mode where we trust the reported system delay
    values the AEC receives. The corresponding define is set appropriately
    in the code, but it can be force-enabled here for testing.

allow_posix_link_time_opt
Current value (from the default) = false
From //build/toolchain/toolchain.gni:17

android_full_debug
Current value (from the default) = false
From //build/config/compiler/BUILD.gn:42

    Normally, Android builds are lightly optimized, even for debug builds, to
    keep binary size down. Setting this flag to true disables such optimization

apm_debug_dump
Current value (from the default) = false
From //webrtc/webrtc.gni:69

    Selects whether debug dumps for the audio processing module
    should be generated.

asan_globals
Current value (from the default) = false
From //build/config/sanitizers/sanitizers.gni:148

    Detect overflow/underflow for global objects.

    Mac: http://crbug.com/352073

auto_profile_path
Current value (from the default) = ""
From //build/config/compiler/BUILD.gn:97

    AFDO (Automatic Feedback Directed Optimizer) is a form of profile-guided
    optimization that GCC supports. It used by ChromeOS in their official
    builds. To use it, set auto_profile_path to the path to a file containing
    the needed gcov profiling data.

binutils_path
Current value (from the default) = "../../third_party/binutils/Linux_x64/Release/bin"
From //build/config/compiler/BUILD.gn:51

build_libsrtp_tests
Current value (from the default) = false
From //third_party/libsrtp/BUILD.gn:10

    Tests may not be appropriate for some build environments, e.g. Windows.
    Rather than enumerate valid options, we just let clients ask for them.

build_with_mozilla
Current value (from the default) = false
From //webrtc/webrtc.gni:89

    Enable to use the Mozilla internal settings.

bundle_pool_depth
Current value (from the default) = -1
From //build/toolchain/mac/BUILD.gn:29

    Reduce the number of tasks using the copy_bundle_data and compile_xcassets
    tools as they can cause lots of I/O contention when invoking ninja with a
    large number of parallel jobs (e.g. when using distributed build like goma).

cc_wrapper
Current value (from the default) = ""
From //build/toolchain/cc_wrapper.gni:36

    Set to "ccache", "icecc" or "distcc".  Probably doesn't work on windows.

chrome_pgo_phase
Current value (from the default) = 0
From //build/config/compiler/pgo/pgo.gni:13

    Specify the current PGO phase.
    Here's the different values that can be used:
        0 : Means that PGO is turned off.
        1 : Used during the PGI (instrumentation) phase.
        2 : Used during the PGO (optimization) phase.

    TODO(sebmarchand): Add support for the PGU (update) phase.

clang_base_path
Current value (from the default) = "//third_party/llvm-build/Release+Asserts"
From //build/config/clang/clang.gni:12

clang_use_chrome_plugins
Current value (from the default) = true
From //build/config/clang/clang.gni:10

    Indicates if the build should use the Chrome-specific plugins for enforcing
    coding guidelines, etc. Only used when compiling with Clang.

clang_version
Current value (from the default) = "6.0.0"
From //build/toolchain/toolchain.gni:67

    Clang compiler version. Clang files are placed at version-dependent paths.

concurrent_links
Current value (from the default) = -1
From //build/toolchain/concurrent_links.gni:19

    Limit the number of concurrent links; we often want to run fewer
    links at once than we do compiles, because linking is memory-intensive.
    The default to use varies by platform and by the amount of memory
    available, so we call out to a script to get the right value.

current_cpu
Current value (from the default) = ""
(Internally set; try `gn help current_cpu`.)

current_os
Current value (from the default) = ""
(Internally set; try `gn help current_os`.)

custom_toolchain
Current value (from the default) = ""
From //build/config/BUILDCONFIG.gn:147

    Allows the path to a custom target toolchain to be injected as a single
    argument, and set as the default toolchain.

dcheck_always_on
Current value (from the default) = false
From //build/config/dcheck_always_on.gni:7

    Set to true to enable dcheck in Release builds.

disable_libfuzzer
Current value (from the default) = false
From //build/config/sanitizers/sanitizers.gni:95

    Helper variable for testing builds with disabled libfuzzer.
    Not for client use.

enable_dsyms
Current value (from the default) = false
From //build/config/mac/symbols.gni:17

    Produce dSYM files for targets that are configured to do so. dSYM
    generation is controlled globally as it is a linker output (produced via
    the //build/toolchain/mac/linker_driver.py. Enabling this will result in
    all shared library, loadable module, and executable targets having a dSYM
    generated.

enable_full_stack_frames_for_profiling
Current value (from the default) = false
From //build/config/compiler/BUILD.gn:59

    Compile in such a way as to make it possible for the profiler to unwind full
    stack frames. Setting this flag has a large effect on the performance of the
    generated code than just setting profiling, but gives the profiler more
    information to analyze.
    Requires profiling to be set to true.

enable_ios_bitcode
Current value (from the default) = false
From //build/config/ios/BUILD.gn:23

    Enabling this option makes clang compile to an intermediate
    representation ("bitcode"), and not to native code. This is preferred
    when including WebRTC in the apps that will be sent to Apple's App Store
    and mandatory for the apps that run on watchOS or tvOS.
    The option only works when building with Xcode (use_xcode_clang = true).
    Mimicking how Xcode handles it, the production builds (is_debug = false)
    get real bitcode sections added, while the debug builds (is_debug = true)
    only get bitcode-section "markers" added in them.
    NOTE: This option is ignored when building versions for the iOS simulator,
    where a part of libvpx is compiled from the assembly code written using
    Intel assembly syntax; Yasm / Nasm do not support emitting bitcode parts.
    That is not a limitation for now as Xcode mandates the presence of bitcode
    only when building bitcode-enabled projects for real devices (ARM CPUs).

enable_iterator_debugging
Current value (from the default) = true
From //build/config/BUILD.gn:34

    When set (the default) enables C++ iterator debugging in debug builds.
    Iterator debugging is always off in release builds (technically, this flag
    affects the "debug" config, which is always available but applied by
    default only in debug builds).

    Iterator debugging is generally useful for catching bugs. But it can
    introduce extra locking to check the state of an iterator against the state
    of the current object. For iterator- and thread-heavy code, this can
    significantly slow execution.

enable_nacl
Current value (from the default) = true
From //build/config/features.gni:27

    Enables Native Client support.
    Temporarily disable nacl on arm64 linux to get rid of compilation errors.
    TODO(mcgrathr): When mipsel-nacl-clang is available, drop the exclusion.

enable_nacl_nonsfi
Current value (from the default) = true
From //build/config/features.gni:32

    Non-SFI is not yet supported on mipsel

enable_precompiled_headers
Current value (from the default) = true
From //build/config/pch.gni:11

    Precompiled header file support is by default available,
    but for distributed build system uses (like goma) or when
    doing official builds.

enable_profiling
Current value (from the default) = false
From //build/config/compiler/compiler.gni:28

    Compile in such a way as to enable profiling of the generated code. For
    example, don't omit the frame pointer and leave in symbols.

enable_resource_whitelist_generation
Current value (from the default) = false
From //build/config/android/config.gni:369

    Enables used resource whitelist generation. Set for official builds only
    as a large amount of build output is generated.

enable_stripping
Current value (from the default) = false
From //build/config/mac/symbols.gni:24

    Strip symbols from linked targets by default. If this is enabled, the
    //build/config/mac:strip_all config will be applied to all linked targets.
    If custom stripping parameters are required, remove that config from a
    linked target and apply custom -Wcrl,strip flags. See
    //build/toolchain/mac/linker_driver.py for more information.

exclude_unwind_tables
Current value (from the default) = false
From //build/config/compiler/BUILD.gn:74

    Omit unwind support in official builds to save space.
    We can use breakpad for these builds.

fatal_linker_warnings
Current value (from the default) = true
From //build/config/compiler/BUILD.gn:86

    Enable fatal linker warnings. Building Chromium with certain versions
    of binutils can cause linker warning.
    See: https://bugs.chromium.org/p/chromium/issues/detail?id=457359

fieldtrial_testing_like_official_build
Current value (from the default) = false
From //build/config/features.gni:56

    Set to true make a build that disables activation of field trial tests
    specified in testing/variations/fieldtrial_testing_config_*.json.
    Note: this setting is ignored if is_chrome_branded.

full_wpo_on_official
Current value (from the default) = false
From //build/config/compiler/compiler.gni:119

gcc_target_rpath
Current value (from the default) = ""
From //build/config/gcc/BUILD.gn:18

    When non empty, overrides the target rpath value. This allows a user to
    make a Chromium build where binaries and shared libraries are meant to be
    installed into separate directories, like /usr/bin/chromium and
    /usr/lib/chromium for instance. It is useful when a build system that
    generates a whole target root filesystem (like Yocto) is used on top of gn,
    especially when cross-compiling.
    Note: this gn arg is similar to gyp target_rpath generator flag.

generate_linker_map
Current value (from the default) = false
From //build/toolchain/toolchain.gni:44

    Used for binary size analysis.
    Currently disabled on LLD because of a bug (fixed upstream).
    See https://crbug.com/716209.

gold_path
Current value (from the default) = false
From //build/config/compiler/BUILD.gn:63

    When we are going to use gold we need to find it.
    This is initialized below, after use_gold might have been overridden.

goma_dir
Current value (from the default) = "/Users/ilong/goma"
From //build/toolchain/goma.gni:17

    Absolute directory containing the gomacc binary.

host_cpu
Current value (from the default) = "x64"
(Internally set; try `gn help host_cpu`.)

host_os
Current value (from the default) = "mac"
(Internally set; try `gn help host_os`.)

host_pkg_config
Current value (from the default) = ""
From //build/config/linux/pkg_config.gni:36

    A optional pkg-config wrapper to use for tools built on the host.

host_toolchain
Current value (from the default) = ""
From //build/config/BUILDCONFIG.gn:151

    This should not normally be set as a build argument.  It's here so that
    every toolchain can pass through the "global" value via toolchain_args().

ios_app_bundle_id_prefix
Current value (from the default) = "org.chromium"
From //build/config/ios/ios_sdk.gni:33

    Prefix for CFBundleIdentifier property of iOS bundles (correspond to the
    "Organization Identifier" in Xcode). Code signing will fail if no mobile
    provisioning for the selected code signing identify support that prefix.

ios_automatically_manage_certs
Current value (from the default) = true
From //build/config/ios/ios_sdk.gni:39

    If true, then allow using Xcode to automatically manage certificates. This
    requires loading a separate Xcode project and enable automatically managed
    certificates. When true, all test application will use the same bundle id
    to avoid running out of certificates if using a free account.

ios_code_signing_identity
Current value (from the default) = ""
From //build/config/ios/ios_sdk.gni:27

ios_code_signing_identity_description
Current value (from the default) = "iPhone Developer"
From //build/config/ios/ios_sdk.gni:28

ios_deployment_target
Current value (from the default) = "9.0"
From //build/config/ios/ios_sdk.gni:21

    Version of iOS that we're targeting.

ios_enable_code_signing
Current value (from the default) = true
From //build/config/ios/ios_sdk.gni:26

    The iOS Code signing identity to use
    TODO(GYP), TODO(sdfresne): Consider having a separate
    ios_enable_code_signing_flag=<bool> flag to make the invocation clearer.

ios_enable_coverage
Current value (from the default) = false
From //build/config/ios/ios_sdk.gni:43

    Enabling this option makes clang compile for profiling to gather code
    coverage metrics.

ios_sdk_name
Current value (from the default) = ""
From //build/config/ios/ios_sdk.gni:11

ios_sdk_path
Current value (from the default) = ""
From //build/config/ios/ios_sdk.gni:10

    SDK path to use. When empty this will use the default SDK based on the
    value of use_ios_simulator.

ios_sdk_platform
Current value (from the default) = ""
From //build/config/ios/ios_sdk.gni:13

ios_sdk_platform_path
Current value (from the default) = ""
From //build/config/ios/ios_sdk.gni:14

ios_sdk_version
Current value (from the default) = ""
From //build/config/ios/ios_sdk.gni:12

is_asan
Current value (from the default) = false
From //build/config/sanitizers/sanitizers.gni:11

    Compile for Address Sanitizer to find memory bugs.

is_cast_audio_only
Current value (from the default) = false
From //build/config/chromecast_build.gni:14

    Set this true for an audio-only Chromecast build.

is_cast_desktop_build
Current value (from the default) = false
From //build/config/chromecast_build.gni:26

    True if Chromecast build is targeted for linux desktop. This type of build
    is useful for testing and development, but currently supports only a subset
    of Cast functionality. Though this defaults to true for x86 Linux devices,
    this should be overriden manually for an embedded x86 build.
    TODO(slan): Remove instances of this when x86 is a fully supported platform.

is_cfi
Current value (from the default) = false
From //build/config/sanitizers/sanitizers.gni:58

    Compile with Control Flow Integrity to protect virtual calls and casts.
    See http://clang.llvm.org/docs/ControlFlowIntegrity.html

    TODO(pcc): Remove this flag if/when CFI is enabled in all official builds.

is_chrome_branded
Current value (from the default) = false
From //build/config/chrome_build.gni:9

    Select the desired branding flavor. False means normal Chromium branding,
    true means official Google Chrome branding (requires extra Google-internal
    resources).

is_chromecast
Current value (from the default) = false
From //build/config/chromecast_build.gni:11

    Set this true for a Chromecast build. Chromecast builds are supported on
    Linux and Android.

is_clang
Current value (from the default) = true
From //build/config/BUILDCONFIG.gn:139

is_component_build
Current value = false
From //.gn:38
Overridden from the default = false
From //build/config/BUILDCONFIG.gn:169

is_debug
Current value (from the default) = true
From //build/config/BUILDCONFIG.gn:158

    Debug build. Enabling official builds automatically sets is_debug to false.

is_desktop_linux
Current value (from the default) = false
From //build/config/BUILDCONFIG.gn:134

    Whether we're a traditional desktop unix.

is_lsan
Current value (from the default) = false
From //build/config/sanitizers/sanitizers.gni:14

    Compile for Leak Sanitizer to find leaks.

is_msan
Current value (from the default) = false
From //build/config/sanitizers/sanitizers.gni:17

    Compile for Memory Sanitizer to find uninitialized reads.

is_multi_dll_chrome
Current value (from the default) = false
From //build/config/chrome_build.gni:13

    Break chrome.dll into multple pieces based on process type. Only available
    on Windows.

is_official_build
Current value (from the default) = false
From //build/config/BUILDCONFIG.gn:131

    Set to enable the official build level of optimization. This has nothing
    to do with branding, but enables an additional level of optimization above
    release (!is_debug). This might be better expressed as a tri-state
    (debug, release, official) but for historical reasons there are two
    separate flags.

is_syzyasan
Current value (from the default) = false
From //build/config/sanitizers/sanitizers.gni:52

    Enable building with SyzyAsan which can find certain types of memory
    errors. Only works on Windows. See
    https://github.com/google/syzygy/wiki/SyzyASanHowTo

is_tsan
Current value (from the default) = false
From //build/config/sanitizers/sanitizers.gni:20

    Compile for Thread Sanitizer to find threading bugs.

is_ubsan
Current value (from the default) = false
From //build/config/sanitizers/sanitizers.gni:24

    Compile for Undefined Behaviour Sanitizer to find various types of
    undefined behaviour (excludes vptr checks).

is_ubsan_no_recover
Current value (from the default) = false
From //build/config/sanitizers/sanitizers.gni:27

    Halt the program if a problem is detected.

is_ubsan_null
Current value (from the default) = false
From //build/config/sanitizers/sanitizers.gni:30

    Compile for Undefined Behaviour Sanitizer's null pointer checks.

is_ubsan_security
Current value (from the default) = false
From //build/config/sanitizers/sanitizers.gni:87

    Enables core ubsan security features. Will later be removed once it matches
    is_ubsan.

is_ubsan_vptr
Current value (from the default) = false
From //build/config/sanitizers/sanitizers.gni:33

    Compile for Undefined Behaviour Sanitizer's vptr checks.

is_win_fastlink
Current value (from the default) = false
From //build/config/compiler/compiler.gni:45

    Tell VS to create a PDB that references information in .obj files rather
    than copying it all. This should improve linker performance. mspdbcmf.exe
    can be used to convert a fastlink pdb to a normal one.

libcpp_is_static
Current value (from the default) = true
From //build/config/c++/c++.gni:33

    ASan, MSan and TSan builds need to override operator new, operator delete,
    and some exception handling symbols, so libc++ must be a shared library to
    prevent duplicate symbol errors when linking.
    Additionally, -fsanitize=vptr requires libc++ to be a shared library
    because the ubsan runtime library that implements -fsanitize=vptr calls
    dynamic_cast with the ABI type info classes, which won't return the right
    answer if each DSO has its own copy of the ABI classes.

libyuv_disable_jpeg
Current value (from the default) = false
From //third_party/libyuv/libyuv.gni:15

libyuv_include_tests
Current value (from the default) = true
From //third_party/libyuv/libyuv.gni:14

libyuv_use_gflags
Current value (from the default) = true
From //third_party/libyuv/BUILD.gn:14

    Set to false to disable building with gflags.

libyuv_use_msa
Current value (from the default) = false
From //third_party/libyuv/libyuv.gni:18

libyuv_use_neon
Current value (from the default) = true
From //third_party/libyuv/libyuv.gni:16

linkrepro_root_dir
Current value (from the default) = ""
From //build/config/compiler/compiler.gni:63

    Root directory that will store the MSVC link repro. This should only be
    used for debugging purposes on the builders where a MSVC linker flakyness
    has been observed. The targets for which a link repro should be generated
    should add somethink like this to their configuration:
      if (linkrepro_root_dir != "") {
        ldflags = ["/LINKREPRO:" + linkrepro_root_dir + "/" + target_name]
      }

    Note that doing a link repro uses a lot of disk space and slows down the
    build, so this shouldn't be enabled on too many targets.

    See crbug.com/669854.

linux_use_bundled_binutils
Current value (from the default) = false
From //build/config/compiler/BUILD.gn:49

llvm_force_head_revision
Current value (from the default) = false
From //build/toolchain/toolchain.gni:34

    If this is set to true, or if LLVM_FORCE_HEAD_REVISION is set to 1
    in the environment, we use the revision in the llvm repo to determine
    the CLANG_REVISION to use, instead of the version hard-coded into
    //tools/clang/scripts/update.py. This should only be used in
    conjunction with setting LLVM_FORCE_HEAD_REVISION in the
    environment when `gclient runhooks` is run as well.

mac_deployment_target
Current value (from the default) = "10.9.0"
From //build/config/mac/mac_sdk.gni:12

    Minimum supported version of macOS. Must be of the form x.x.x for
    Info.plist files.

mac_sdk_min
Current value = "10.11"
From //.gn:40
Overridden from the default = "10.12"
From //build/config/mac/mac_sdk_overrides.gni:12

mac_sdk_name
Current value (from the default) = "macosx"
From //build/config/mac/mac_sdk.gni:20

    The SDK name as accepted by xcodebuild.

mac_sdk_path
Current value (from the default) = ""
From //build/config/mac/mac_sdk.gni:17

    Path to a specific version of the Mac SDK, not including a slash at the end.
    If empty, the path to the lowest version greater than or equal to
    mac_sdk_min is used.

machine_os_build
Current value (from the default) = ""
From //build/config/ios/ios_sdk.gni:18

msan_track_origins
Current value (from the default) = 2
From //build/config/sanitizers/sanitizers.gni:38

    Track where uninitialized memory originates from. From fastest to slowest:
    0 - no tracking, 1 - track only the initial allocation site, 2 - track the
    chain of stores leading from allocation site to use site.

msvc_use_absolute_paths
Current value (from the default) = false
From //build/toolchain/toolchain.gni:48

    Use absolute file paths in the compiler diagnostics and __FILE__ macro
    if needed.

optimize_for_fuzzing
Current value (from the default) = false
From //build/config/compiler/BUILD.gn:101

    Optimize for coverage guided fuzzing (balance between speed and number of
    branches)

optimize_for_size
Current value (from the default) = false
From //build/config/compiler/BUILD.gn:81

    If true, optimize for size. Does not affect windows builds.
    Linux & Mac favor speed over size.
    TODO(brettw) it's weird that Mac and desktop Linux are different. We should
    explore favoring size over speed in this case as well.

pgo_data_path
Current value (from the default) = ""
From //build/config/compiler/pgo/pgo.gni:16

    When using chrome_pgo_phase = 2, read profile data from this path.

pkg_config
Current value (from the default) = ""
From //build/config/linux/pkg_config.gni:33

    A pkg-config wrapper to call instead of trying to find and call the right
    pkg-config directly. Wrappers like this are common in cross-compilation
    environments.
    Leaving it blank defaults to searching PATH for 'pkg-config' and relying on
    the sysroot mechanism to find the right .pc files.

proprietary_codecs
Current value (from the default) = false
From //build/config/features.gni:39

    Enables proprietary codecs and demuxers; e.g. H264, AAC, MP3, and MP4.
    We always build Google Chrome and Chromecast with proprietary codecs.

    Note: this flag is used by WebRTC which is DEPSed into Chrome. Moving it
    out of //build will require using the build_overrides directory.

rtc_audio_device_plays_sinus_tone
Current value (from the default) = false
From //webrtc/webrtc.gni:157

    When set to true, replace the audio output with a sinus tone at 440Hz.
    The ADM will ask for audio data from WebRTC but instead of reading real
    audio samples from NetEQ, a sinus tone will be generated and replace the
    real audio samples.

rtc_build_json
Current value (from the default) = true
From //webrtc/webrtc.gni:78

    Disable these to not build components which can be externally provided.

rtc_build_libevent
Current value (from the default) = false
From //webrtc/webrtc.gni:115

rtc_build_libsrtp
Current value (from the default) = true
From //webrtc/webrtc.gni:79

rtc_build_libvpx
Current value (from the default) = true
From //webrtc/webrtc.gni:80

rtc_build_libyuv
Current value (from the default) = true
From //webrtc/webrtc.gni:82

rtc_build_openmax_dl
Current value (from the default) = true
From //webrtc/webrtc.gni:83

rtc_build_opus
Current value (from the default) = true
From //webrtc/webrtc.gni:84

rtc_build_ssl
Current value (from the default) = true
From //webrtc/webrtc.gni:85

rtc_build_usrsctp
Current value (from the default) = true
From //webrtc/webrtc.gni:86

rtc_build_with_neon
Current value (from the default) = true
From //webrtc/webrtc.gni:134

rtc_enable_android_opensl
Current value (from the default) = false
From //webrtc/webrtc.gni:91

rtc_enable_bwe_test_logging
Current value (from the default) = false
From //webrtc/webrtc.gni:72

    Set this to true to enable BWE test logging.

rtc_enable_external_auth
Current value (from the default) = false
From //webrtc/webrtc.gni:65

    Enable when an external authentication mechanism is used for performing
    packet authentication for RTP packets instead of libsrtp.

rtc_enable_intelligibility_enhancer
Current value (from the default) = false
From //webrtc/webrtc.gni:61

    Disable the code for the intelligibility enhancer by default.

rtc_enable_libevent
Current value (from the default) = false
From //webrtc/webrtc.gni:114

rtc_enable_protobuf
Current value (from the default) = true
From //webrtc/webrtc.gni:58

    Enables the use of protocol buffers for debug recordings.

rtc_enable_sctp
Current value (from the default) = true
From //webrtc/webrtc.gni:75

    Set this to disable building with support for SCTP data channels.

rtc_include_ilbc
Current value (from the default) = true
From //webrtc/webrtc.gni:180

    Include the iLBC audio codec?

rtc_include_internal_audio_device
Current value (from the default) = true
From //webrtc/webrtc.gni:189

    Chromium uses its own IO handling, so the internal ADM is only built for
    standalone WebRTC.

rtc_include_opus
Current value (from the default) = true
From //webrtc/webrtc.gni:37

    Disable this to avoid building the Opus audio codec.

rtc_include_pulse_audio
Current value (from the default) = true
From //webrtc/webrtc.gni:185

    Excluded in Chromium since its prerequisites don't require Pulse Audio.

rtc_include_tests
Current value (from the default) = true
From //webrtc/webrtc.gni:192

    Include tests in standalone checkout.

rtc_initialize_ffmpeg
Current value (from the default) = true
From //webrtc/webrtc.gni:168

    FFmpeg must be initialized for |H264DecoderImpl| to work. This can be done
    by WebRTC during |H264DecoderImpl::InitDecode| or externally. FFmpeg must
    only be initialized once. Projects that initialize FFmpeg externally, such
    as Chromium, must turn this flag off so that WebRTC does not also
    initialize.

rtc_jsoncpp_root
Current value (from the default) = "//third_party/jsoncpp/source/include"
From //webrtc/webrtc.gni:48

    Used to specify an external Jsoncpp include path when not compiling the
    library that comes with WebRTC (i.e. rtc_build_json == 0).

rtc_libvpx_build_vp9
Current value (from the default) = true
From //webrtc/webrtc.gni:81

rtc_link_task_queue_impl
Current value (from the default) = true
From //webrtc/webrtc.gni:108

    Links a default implementation of task queues to targets
    that depend on the target rtc_task_queue. Set to false to
    use an external implementation.

rtc_opus_support_120ms_ptime
Current value (from the default) = true
From //webrtc/webrtc.gni:41

    Enable this if the Opus version upon which WebRTC is built supports direct
    encoding of 120 ms packets.

rtc_opus_variable_complexity
Current value (from the default) = false
From //webrtc/webrtc.gni:44

    Enable this to let the Opus audio codec change complexity on the fly.

rtc_prefer_fixed_point
Current value (from the default) = true
From //webrtc/webrtc.gni:122

rtc_restrict_logging
Current value (from the default) = false
From //webrtc/webrtc.gni:182

rtc_sanitize_coverage
Current value (from the default) = ""
From //webrtc/webrtc.gni:103

    Set to "func", "block", "edge" for coverage generation.
    At unit test runtime set UBSAN_OPTIONS="coverage=1".
    It is recommend to set include_examples=0.
    Use llvm's sancov -html-report for human readable reports.
    See http://clang.llvm.org/docs/SanitizerCoverage.html .

rtc_ssl_root
Current value (from the default) = ""
From //webrtc/webrtc.gni:52

    Used to specify an external OpenSSL include path when not compiling the
    library that comes with WebRTC (i.e. rtc_build_ssl == 0).

rtc_use_dummy_audio_file_devices
Current value (from the default) = false
From //webrtc/webrtc.gni:151

    By default, use normal platform audio support or dummy audio, but don't
    use file-based audio playout and record.

rtc_use_gtk
Current value (from the default) = true
From //webrtc/webrtc.gni:172

    Build sources requiring GTK. NOTICE: This is not present in Chrome OS
    build environments, even if available for Chromium builds.

rtc_use_h264
Current value (from the default) = false
From //webrtc/webrtc.gni:144

    Enable this to build OpenH264 encoder/FFmpeg decoder. This is supported on
    all platforms except Android and iOS. Because FFmpeg can be built
    with/without H.264 support, |ffmpeg_branding| has to separately be set to a
    value that includes H.264, for example "Chrome". If FFmpeg is built without
    H.264, compilation succeeds but |H264DecoderImpl| fails to initialize. See
    also: |rtc_initialize_ffmpeg|.
    CHECK THE OPENH264, FFMPEG AND H.264 LICENSES/PATENTS BEFORE BUILDING.
    http://www.openh264.org, https://www.ffmpeg.org/

rtc_use_lto
Current value (from the default) = false
From //webrtc/webrtc.gni:96

    Link-Time Optimizations.
    Executes code generation at link-time instead of compile-time.
    https://gcc.gnu.org/wiki/LinkTimeOptimization

rtc_use_memcheck
Current value (from the default) = false
From //webrtc/webrtc.gni:161

    When set to true, test targets will declare the files needed to run memcheck
    as data dependencies. This is to enable memcheck execution on swarming bots.

rtc_use_metal_rendering
Current value (from the default) = true
From //webrtc/sdk/BUILD.gn:17

    Determine whether or not to include metal rendering

rtc_use_openmax_dl
Current value (from the default) = false
From //webrtc/webrtc.gni:129

rtc_use_quic
Current value (from the default) = false
From //webrtc/webrtc.gni:147

    Determines whether QUIC code will be built.

safe_browsing_mode
Current value (from the default) = 1
From //build/config/features.gni:50

sanitizer_coverage_flags
Current value (from the default) = ""
From //build/config/sanitizers/sanitizers.gni:103

    Value for -fsanitize-coverage flag. Setting this causes
    use_sanitizer_coverage to be enabled.
    Default value when unset and use_afl=true or use_libfuzzer=true:
        trace-pc-guard
    Default value when unset and use_sanitizer_coverage=true:
        trace-pc-guard,indirect-calls

sanitizer_keep_symbols
Current value (from the default) = false
From //build/config/sanitizers/sanitizers.gni:109

    Keep symbol level when building with sanitizers. When sanitizers are
    enabled, the default is to compile with the minimum debug info level
    necessary, overriding any other symbol level arguments that may be set.
    Setting this to true prevents this.

strip_absolute_paths_from_debug_symbols
Current value (from the default) = false
From //build/config/compiler/BUILD.gn:106

    Optimize symbol files for maximizing goma cache hit rate. This isn't
    on by default when goma is enabled because setting this to true may make
    it harder to debug binaries.

symbol_level
Current value (from the default) = -1
From //build/config/compiler/compiler.gni:24

    How many symbols to include in the build. This affects the performance of
    the build since the symbols are large and dealing with them is slow.
      2 means regular build with symbols.
      1 means minimal symbols, usually enough for backtraces only. Symbols with
    internal linkage (static functions or those in anonymous namespaces) may not
    appear when using this level.
      0 means no symbols.
      -1 means auto-set according to debug/release and platform.

system_libdir
Current value (from the default) = "lib"
From //build/config/linux/pkg_config.gni:47

    CrOS systemroots place pkgconfig files at <systemroot>/usr/share/pkgconfig
    and one of <systemroot>/usr/lib/pkgconfig or <systemroot>/usr/lib64/pkgconfig
    depending on whether the systemroot is for a 32 or 64 bit architecture.

    When build under GYP, CrOS board builds specify the 'system_libdir' variable
    as part of the GYP_DEFINES provided by the CrOS emerge build or simple
    chrome build scheme. This variable permits controlling this for GN builds
    in similar fashion by setting the `system_libdir` variable in the build's
    args.gn file to 'lib' or 'lib64' as appropriate for the target architecture.

target_cpu
Current value = "arm64"
From //out/ios/args.gn:2
Overridden from the default = ""
(Internally set; try `gn help target_cpu`.)

target_os
Current value = "ios"
From //out/ios/args.gn:1
Overridden from the default = ""
(Internally set; try `gn help target_os`.)

target_sysroot
Current value (from the default) = ""
From //build/config/sysroot.gni:13

    The absolute path of the sysroot that is applied when compiling using
    the target toolchain.

target_sysroot_dir
Current value (from the default) = "//build/linux"
From //build/config/sysroot.gni:16

    The absolute path to directory containing linux sysroot images

toolkit_views
Current value (from the default) = true
From //build/config/ui.gni:42

    True means the UI is built using the "views" framework.

treat_warnings_as_errors
Current value (from the default) = true
From //build/config/compiler/BUILD.gn:38

    Default to warnings as errors for default workflow, where we catch
    warnings with known toolchains. Allow overriding this e.g. for Chromium
    builds on Linux that could use a different version of the compiler.
    With GCC, warnings in no-Chromium code are always not treated as errors.

use_afl
Current value (from the default) = false
From //build/config/sanitizers/sanitizers.gni:83

    Compile for fuzzing with AFL.

use_allocator
Current value (from the default) = "none"
From //build/config/allocator.gni:29

    Memory allocator to use. Set to "none" to use default allocator.

use_allocator_shim
Current value (from the default) = true
From //build/config/allocator.gni:32

    Causes all the allocations to be routed via allocator_shim.cc.

use_ash
Current value (from the default) = false
From //build/config/ui.gni:25

    Indicates if Ash is enabled. Ash is the Aura Shell which provides a
    desktop-like environment for Aura. Requires use_aura = true

use_aura
Current value (from the default) = false
From //build/config/ui.gni:34

    Indicates if Aura is enabled. Aura is a low-level windowing library, sort
    of a replacement for GDI or GTK.

use_cfi_cast
Current value (from the default) = false
From //build/config/sanitizers/sanitizers.gni:64

    Enable checks for bad casts: derived cast and unrelated cast.
    TODO(krasin): remove this, when we're ready to add these checks by default.
    https://crbug.com/626794

use_cfi_diag
Current value (from the default) = false
From //build/config/sanitizers/sanitizers.gni:72

    Print detailed diagnostics when Control Flow Integrity detects a violation.

use_cfi_icall
Current value (from the default) = false
From //build/config/sanitizers/sanitizers.gni:69

    Enable checks for indirect function calls via a function pointer.
    TODO(pcc): remove this when we're ready to add these checks by default.
    https://crbug.com/701919

use_cfi_recover
Current value (from the default) = false
From //build/config/sanitizers/sanitizers.gni:76

    Let Control Flow Integrity continue execution instead of crashing when
    printing diagnostics (use_cfi_diag = true).

use_clang_static_analyzer
Current value (from the default) = false
From //build/toolchain/clang_static_analyzer.gni:10

    Uses the Clang static analysis tools during compilation.

use_custom_libcxx
Current value (from the default) = false
From //build/config/c++/c++.gni:14

use_custom_libcxx_for_host
Current value (from the default) = false
From //build/config/c++/c++.gni:24

    Use libc++ instead of stdlibc++ when using the host_cpu toolchain, even if
    use_custom_libcxx is false. This is useful for cross-compiles where a custom
    toolchain for the target_cpu has been set as the default toolchain, but
    use_custom_libcxx should still be true when building for the host.  The
    expected usage is to set use_custom_libcxx=false and
    use_custom_libcxx_for_host=true in the passed in buildargs.

use_cxx11
Current value = true
From //.gn:43
Overridden from the default = false
From //build/config/compiler/BUILD.gn:109

    Allow projects that wish to stay on C++11 to override Chromium's default.

use_cxx11_on_android
Current value = false
From //.gn:46
Overridden from the default = true
From //build/config/compiler/BUILD.gn:114

    C++11 may not be an option if Android test infrastructure is used.

use_dbus
Current value (from the default) = false
From //build/config/features.gni:61

use_debug_fission
Current value (from the default) = "default"
From //build/config/compiler/compiler.gni:40

    use_debug_fission: whether to use split DWARF debug info
    files. This can reduce link time significantly, but is incompatible
    with some utilities such as icecc and ccache. Requires gold and
    gcc >= 4.8 or clang.
    http://gcc.gnu.org/wiki/DebugFission

    This is a placeholder value indicating that the code below should set
    the default.  This is necessary to delay the evaluation of the default
    value expression until after its input values such as use_gold have
    been set, e.g. by a toolchain_args() block.

use_drfuzz
Current value (from the default) = false
From //build/config/sanitizers/sanitizers.gni:91

    Compile for fuzzing with Dr. Fuzz
    See http://www.chromium.org/developers/testing/dr-fuzz

use_gconf
Current value (from the default) = false
From //build/config/features.gni:65

    Option controlling the use of GConf (the classic GNOME configuration
    system).

use_gio
Current value (from the default) = false
From //build/config/features.gni:68

use_glib
Current value (from the default) = false
From //build/config/ui.gni:37

    Whether we should use glib, a low level C utility library.

use_gold
Current value (from the default) = false
From //build/config/compiler/compiler.gni:134

use_goma
Current value (from the default) = false
From //build/toolchain/goma.gni:9

    Set to true to enable distributed compilation using Goma.

use_incremental_wpo
Current value (from the default) = false
From //build/config/compiler/compiler.gni:49

    Whether or not we should turn on incremental WPO. Only affects the VS
    Windows build.

use_libfuzzer
Current value (from the default) = false
From //build/config/sanitizers/sanitizers.gni:80

    Compile for fuzzing with LLVM LibFuzzer.
    See http://www.chromium.org/developers/testing/libfuzzer

use_lld
Current value (from the default) = false
From //build/config/compiler/compiler.gni:126

    Set to true to use lld, the LLVM linker. This flag may be used on Windows,
    Linux or Fuchsia.

use_locally_built_instrumented_libraries
Current value (from the default) = false
From //build/config/sanitizers/sanitizers.gni:47

    Use dynamic libraries instrumented by one of the sanitizers instead of the
    standard system libraries. Set this flag to build the libraries from source.

use_ozone
Current value (from the default) = false
From //build/config/ui.gni:30

    Indicates if Ozone is enabled. Ozone is a low-level library layer for Linux
    that does not require X11. Enabling this feature disables use of glib, x11,
    Pango, and Cairo.

use_pic
Current value (from the default) = true
From //build/config/compiler/compiler.gni:66

    Whether or not we should use position independent code.

use_prebuilt_instrumented_libraries
Current value (from the default) = false
From //build/config/sanitizers/sanitizers.gni:43

    Use dynamic libraries instrumented by one of the sanitizers instead of the
    standard system libraries. Set this flag to download prebuilt binaries from
    GCS.

use_rtti
Current value (from the default) = false
From //build/config/compiler/BUILD.gn:91

    Build with C++ RTTI enabled. Chromium builds without RTTI by default,
    but some sanitizers are known to require it, like CFI diagnostics
    and UBsan variants.

use_sanitizer_coverage
Current value (from the default) = false
From //build/config/sanitizers/sanitizers.gni:143

use_sysroot
Current value (from the default) = true
From //build/config/sysroot.gni:19

use_thin_lto
Current value (from the default) = false
From //build/toolchain/toolchain.gni:25

    If used with allow_posix_link_time_opt, it enables support for ThinLTO,
    which links 3x-10x faster than full LTO. See also
    http://blog.llvm.org/2016/06/thinlto-scalable-and-incremental-lto.html

use_udev
Current value (from the default) = false
From //build/config/features.gni:59

    libudev usage. This currently only affects the content layer.

use_xcode_clang
Current value (from the default) = false
From //build/toolchain/toolchain.gni:39

    Compile with Xcode version of clang instead of hermetic version shipped
    with the build. Used on iOS to ship official builds (as they are built
    with the version of clang shipped with Xcode).

v8_current_cpu
Current value (from the default) = "arm64"
From //build/config/v8_target_cpu.gni:60

    This argument is declared here so that it can be overridden in toolchains.
    It should never be explicitly set by the user.

v8_target_cpu
Current value (from the default) = ""
From //build/config/v8_target_cpu.gni:33

    This arg is used when we want to tell the JIT-generating v8 code
    that we want to have it generate for an architecture that is different
    than the architecture that v8 will actually run on; we then run the
    code under an emulator. For example, we might run v8 on x86, but
    generate arm code and run that under emulation.

    This arg is defined here rather than in the v8 project because we want
    some of the common architecture-specific args (like arm_float_abi or
    mips_arch_variant) to be set to their defaults either if the current_cpu
    applies *or* if the v8_current_cpu applies.

    As described below, you can also specify the v8_target_cpu to use
    indirectly by specifying a `custom_toolchain` that contains v8_$cpu in the
    name after the normal toolchain.

    For example, `gn gen --args="custom_toolchain=...:clang_x64_v8_arm64"`
    is equivalent to setting --args=`v8_target_cpu="arm64"`. Setting
    `custom_toolchain` is more verbose but makes the toolchain that is
    (effectively) being used explicit.

    v8_target_cpu can only be used to target one architecture in a build,
    so if you wish to build multiple copies of v8 that are targeting
    different architectures, you will need to do something more
    complicated involving multiple toolchains along the lines of
    custom_toolchain, above.

xcode_build
Current value (from the default) = ""
From //build/config/ios/ios_sdk.gni:17

xcode_version
Current value (from the default) = ""
From //build/config/ios/ios_sdk.gni:15

xcode_version_int
Current value (from the default) = 0
From //build/config/ios/ios_sdk.gni:16
————————————————
版权声明：本文为 CSDN 博主「liwenlong_only」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/liwenlong_only/article/details/85063168
