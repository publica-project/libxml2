workspace(name = "com_getpublica_libxml2")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")

#
# Golang
#

# TODO: gogo 1.1.1 is generating three extra fields that are breaking Gorm
# 	XXX_NoUnkeyedLiteral struct{} `json:"-"`
# 	XXX_unrecognized     []byte   `json:"-"`
# 	XXX_sizecache        int32    `json:"-"`
# http_archive(
#     name = "io_bazel_rules_go",
#     sha256 = "5f3b0304cdf0c505ec9e5b3c4fc4a87b5ca21b13d8ecc780c97df3d1809b9ce6",
#     urls = ["https://github.com/bazelbuild/rules_go/releases/download/0.15.1/rules_go-0.15.1.tar.gz"],
# )
http_archive(
    name = "io_bazel_rules_go",
    sha256 = "7d306fdc47a19f24d571ee8f000874cc57ed7903b7314ae73d3ce0d92ef2f36e",
    strip_prefix = "rules_go-d34828bbe7bc1481c616e21541b39b032de61d66",
    urls = ["https://github.com/publica-project/rules_go/archive/d34828bbe7bc1481c616e21541b39b032de61d66.zip"],
)

http_archive(
    name = "bazel_gazelle",
    sha256 = "c0a5739d12c6d05b6c1ad56f2200cb0b57c5a70e03ebd2f7b87ce88cabf09c7b",
    urls = ["https://github.com/bazelbuild/bazel-gazelle/releases/download/0.14.0/bazel-gazelle-0.14.0.tar.gz"],
)

http_archive(
    name = "com_github_jmhodges_bazel_gomock",
    sha256 = "dbf6358d17923534f09d2cc5402bb05efe38795be777389c7d13d3c94e0a3f6d",
    strip_prefix = "bazel_gomock-5b73edb74e569ff404b3beffc809d6d9f205e0e4",
    urls = ["https://github.com/jmhodges/bazel_gomock/archive/5b73edb74e569ff404b3beffc809d6d9f205e0e4.zip"],
)

#
# Docker
#

http_archive(
    name = "io_bazel_rules_docker",
    sha256 = "29d109605e0d6f9c892584f07275b8c9260803bf0c6fcb7de2623b2bedc910bd",
    strip_prefix = "rules_docker-0.5.1",
    urls = ["https://github.com/bazelbuild/rules_docker/archive/v0.5.1.tar.gz"],
)

#
# Golang
#

load("@io_bazel_rules_go//go:def.bzl", "go_register_toolchains", "go_rules_dependencies", "go_wrap_sdk")

#
# Tools
#

http_archive(
    name = "com_github_bazelbuild_buildtools",
    sha256 = "76d1837a86fa6ef5b4a07438f8489f00bfa1b841e5643b618e01232ba884b1fe",
    strip_prefix = "buildtools-0.15.0",
    url = "https://github.com/bazelbuild/buildtools/archive/0.15.0.zip",
)

go_rules_dependencies()

go_register_toolchains(go_version = "host")

load(
    "@bazel_gazelle//:deps.bzl",
    "gazelle_dependencies",
    "go_repository",
)

gazelle_dependencies()

# This go_repository is used by the com_github_jmhodges_bazel_gomock Bazel plugin
go_repository(
    name = "com_github_golang_mock",
    commit = "c34cdb4725f4c3844d095133c6e40e448b86589b",
    importpath = "github.com/golang/mock",
)

#
# Docker
#

load("@io_bazel_rules_docker//container:pull.bzl", "container_pull")

load(
    "@io_bazel_rules_docker//go:image.bzl",
    _go_image_repos = "repositories",
)

_go_image_repos()

#
# Tools
#

load("@com_github_bazelbuild_buildtools//buildifier:deps.bzl", "buildifier_dependencies")

buildifier_dependencies()

go_repository(
    name = "com_github_pkg_errors",
    commit = "645ef00459ed84a119197bfb8d8205042c6df63d",
    importpath = "github.com/pkg/errors",
)

go_repository(
    name = "com_github_stretchr_testify",
    commit = "12b6f73e6084dad08a7c6e575284b177ecafbc71",
    importpath = "github.com/stretchr/testify",
)

go_repository(
    name = "in_gopkg_xmlpath_v1",
    commit = "a146725ea6e7e357ca683ef3e02e8a403742b9c0",
    importpath = "gopkg.in/xmlpath.v1",
)

#
# Third Party
#

http_archive(
    name = "libxml_archive",
    build_file = "@//:libxml.BUILD",
    sha256 = "f63c5e7d30362ed28b38bfa1ac6313f9a80230720b7fb6c80575eeab3ff5900c",
    strip_prefix = "libxml2-2.9.7",
    urls = [
        "https://mirror.bazel.build/xmlsoft.org/sources/libxml2-2.9.7.tar.gz",
        "http://xmlsoft.org/sources/libxml2-2.9.7.tar.gz",
    ],
)

http_archive(
    name = "zlib_archive",
    build_file = "@//:zlib.BUILD",
    sha256 = "c3e5e9fdd5004dcb542feda5ee4f0ff0744628baf8ed2dd5d66f8ca1197cb1a1",
    strip_prefix = "zlib-1.2.11",
    urls = [
        "https://mirror.bazel.build/zlib.net/zlib-1.2.11.tar.gz",
        "https://zlib.net/zlib-1.2.11.tar.gz",
    ],
)

