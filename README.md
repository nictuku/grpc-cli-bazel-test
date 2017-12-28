# `gprc_cli`  does not currently build if the grpc repo is used from another bazel repository.

Repro:
```
bazel build @com_github_grpc_grpc//test/cpp/util:grpc_cli
```

Current output:

```
ERROR: (12-27 21:49:06.225) /Users/yves/workspace/cache/b632e528b7657b271e4465cc6ae42619/external/com_github_grpc_grpc/src/proto/grpc/reflection/v1alpha/BUILD:21:1: output 'external/com_github_grpc_grpc/src/proto/grpc/reflection/v1alpha/proto/grpc/reflection/v1alpha/reflection.pb.h' was not created.
ERROR: (12-27 21:49:06.226) /Users/yves/workspace/cache/b632e528b7657b271e4465cc6ae42619/external/com_github_grpc_grpc/src/proto/grpc/reflection/v1alpha/BUILD:21:1: output 'external/com_github_grpc_grpc/src/proto/grpc/reflection/v1alpha/proto/grpc/reflection/v1alpha/reflection.pb.cc' was not created.
ERROR: (12-27 21:49:06.227) /Users/yves/workspace/cache/b632e528b7657b271e4465cc6ae42619/external/com_github_grpc_grpc/src/proto/grpc/reflection/v1alpha/BUILD:21:1: not all outputs were created or valid.
ERROR: (12-27 21:49:06.239) /Users/yves/workspace/cache/b632e528b7657b271e4465cc6ae42619/external/com_github_grpc_grpc/src/proto/grpc/reflection/v1alpha/BUILD:21:1: output 'external/com_github_grpc_grpc/src/proto/grpc/reflection/v1alpha/proto/grpc/reflection/v1alpha/reflection.grpc.pb.h' was not created.
ERROR: (12-27 21:49:06.240) /Users/yves/workspace/cache/b632e528b7657b271e4465cc6ae42619/external/com_github_grpc_grpc/src/proto/grpc/reflection/v1alpha/BUILD:21:1: output 'external/com_github_grpc_grpc/src/proto/grpc/reflection/v1alpha/proto/grpc/reflection/v1alpha/reflection.grpc.pb.cc' was not created.
Target @com_github_grpc_grpc//test/cpp/util:grpc_cli failed to build
```

```
$ uname -a
Darwin MacBook-Air.local 17.3.0 Darwin Kernel Version 17.3.0: Thu Nov  9 18:09:22 PST 2017; root:xnu-4570.31.3~1/RELEASE_X86_64 x86_64
```
