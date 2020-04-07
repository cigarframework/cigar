load("@io_bazel_rules_go//go:def.bzl", "go_library")
load("@io_bazel_rules_go//proto:def.bzl", "go_proto_library")

# gazelle:resolve proto github.com/gogo/protobuf/gogoproto/gogo.proto @gogo_special_proto//github.com/gogo/protobuf/gogoproto
# gazelle:resolve proto go github.com/gogo/protobuf/gogoproto/gogo.proto @com_github_gogo_protobuf//gogoproto:go_default_library
proto_library(
    name = "wsproto_proto",
    srcs = ["ws.proto"],
    visibility = ["//visibility:public"],
    deps = [
        "@com_google_protobuf//:any_proto",
        "@gogo_special_proto//github.com/gogo/protobuf/gogoproto",
    ],
)

# gazelle:go_proto_compilers @io_bazel_rules_go//proto:gogoslick_proto
go_proto_library(
    name = "wsproto_go_proto",
    compilers = ["@io_bazel_rules_go//proto:gogoslick_proto"],
    importpath = "github.com/cigarframework/cigar/pkg/wsproto",
    proto = ":wsproto_proto",
    visibility = ["//visibility:public"],
    deps = [
        "@com_github_gogo_protobuf//gogoproto:go_default_library",
    ],
)

go_library(
    name = "go_default_library",
    embed = [":wsproto_go_proto"],
    importpath = "github.com/cigarframework/cigar/pkg/wsproto",
    visibility = ["//visibility:public"],
)
