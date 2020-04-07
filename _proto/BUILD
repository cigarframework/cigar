load("@io_bazel_rules_go//go:def.bzl", "go_library")
load("@io_bazel_rules_go//proto:def.bzl", "go_proto_library")

# gazelle:resolve proto github.com/gogo/protobuf/gogoproto/gogo.proto @gogo_special_proto//github.com/gogo/protobuf/gogoproto
# gazelle:resolve proto go github.com/gogo/protobuf/gogoproto/gogo.proto @com_github_gogo_protobuf//gogoproto:go_default_library
proto_library(
    name = "proto_proto",
    srcs = [
        "arbitrary.proto",
        "echo.proto",
    ],
    visibility = ["//visibility:public"],
    deps = ["@gogo_special_proto//github.com/gogo/protobuf/gogoproto"],
)

# gazelle:go_grpc_compilers @io_bazel_rules_go//proto:gogoslick_grpc,//pkg/protoc-gen-ws:plugin
go_proto_library(
    name = "proto_go_proto",
    compilers = [
        "@io_bazel_rules_go//proto:gogoslick_grpc",
        "//pkg/protoc-gen-ws:plugin",
    ],
    importpath = "github.com/cigarframework/cigar/pkg/proto",
    proto = ":proto_proto",
    visibility = ["//visibility:public"],
    deps = [
        "//_wsproto:go_default_library",  #keep
        "//pkg/wsgrpc:go_default_library",  #keep
        "@com_github_gogo_protobuf//gogoproto:go_default_library",
        "@org_golang_google_grpc//:go_default_library",  #keep
        "@org_golang_google_grpc//metadata:go_default_library",  #keep
        "@org_golang_google_grpc//status:go_default_library",  #keep
    ],
)

go_library(
    name = "go_default_library",
    embed = [":proto_go_proto"],
    importpath = "github.com/cigarframework/cigar/pkg/proto",
    visibility = ["//visibility:public"],
)
