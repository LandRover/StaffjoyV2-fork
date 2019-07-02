# The native http_archive rule is deprecated in Bazel 0.20.0
# we need to load the new rule from the following package
load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive", "http_file")
load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository", "new_git_repository")

io_rules_docker_version="3732c9d05315bef6a3dbd195c545d6fea3b86880" # v0.7.0
## Load docker rules
http_archive(
    name = "io_bazel_rules_docker",
    urls = ["https://github.com/bazelbuild/rules_docker/archive/%s.zip"% io_rules_docker_version],
    type = "zip",
    strip_prefix = "rules_docker-%s" % io_rules_docker_version
)

#DOCKER STUFF
load(
    "@io_bazel_rules_docker//repositories:repositories.bzl",
    container_repositories = "repositories",
)
container_repositories()

load(
    "@io_bazel_rules_docker//container:container.bzl",
    "container_pull",
)

container_repositories()

container_pull(
    name = "nginx",
    registry ="index.docker.io",
    repository = "library/nginx",
    tag = "latest",
)

container_pull(
    name = "ubuntu",
    registry ="index.docker.io",
    repository = "library/ubuntu",
    tag = "xenial",
)


# what is that good for anyway?
#new_http_archive(
#  name = "docker_ubuntu",
#  build_file = "//:BUILD.ubuntu",
#  urls = ["https://codeload.github.com/tianon/docker-brew-ubuntu-core/zip/52c8214ecac89d45592d16ce7c14ef82ac7b0822"],
#  sha256 = "a7386a64ad61298ee518885b414f70f9dba86eda61aebc1bca99bd91b07dd32c",
#  type = "zip",
#  strip_prefix = "docker-brew-ubuntu-core-52c8214ecac89d45592d16ce7c14ef82ac7b0822"
#)

# NGINX

#http_file(
#    name = "nginx",
#    urls = ["http://nginx.org/packages/ubuntu/pool/nginx/n/nginx/nginx_1.10.1-1~xenial_amd64.deb"],
#    sha256 = "18dc0565965bd569b98c575d75d0e130d9794a3f7e7642129c488b515cbdf02c",
#)

# NODEJS

http_file(
    name = "nodejs",
    urls = ["https://deb.nodesource.com/node_6.x/pool/main/n/nodejs/nodejs-dbg_6.4.0-1nodesource1~xenial1_amd64.deb"],
    sha256 = "895dab136994f95d4c7e162e7773239264165921097a7dbf94061dd0e794f538",
)

# GOLANG INIT
load("//tools/go:go_configure.bzl", "go_configure")

go_configure()

bind(
    name = "go_package_prefix",
    actual = "//:go_package_prefix",
)

# GOLANG DEPS

new_git_repository(
    name = "go_recaptcha",
    build_file = "//:third_party/go/dpapathanasiou_recaptcha.BUILD",
    commit = "be5090b17804c90a577d345b6d67acbf01dc90ed", # Jan 21, 2019 (LATEST)
    remote = "https://github.com/dpapathanasiou/go-recaptcha.git",
)

new_git_repository(
    name = "go_libphonenumber",
    build_file = "//:third_party/go/ttacon_libphonenumber.BUILD",
    commit = "23ddf903e8f8800d2857645eb155ffbe15cd02ee", ## Jan 8, 2019 (LATEST GIT COMMIT)
    remote = "https://github.com/ttacon/libphonenumber.git",
)

new_git_repository(
    name = "go_builder",
    build_file = "//:third_party/go/ttacon_builder.BUILD",
    commit = "c099f663e1c235176c175644792c5eb282017ad7", # May 18, 2017 (LATEST GIT COMMIT)
    remote = "https://github.com/ttacon/builder.git",
)

new_git_repository(
    name = "go_jwt",
    build_file = "//:third_party/go/dgrijalva_jwt.BUILD",
    commit = "06ea1031745cb8b3dab3f6a236daf2b0aa468b7e", # v3.2.0 Mar 9, 2018 (LATEST OFFICIAL VERSION)
    remote = "https://github.com/dgrijalva/jwt-go.git",
)

new_git_repository(
    name = "go_gorilla_sessions",
    build_file = "//:third_party/go/gorilla_sessions.BUILD",
    commit = "f57b7e2d29c6211d16ffa52a0998272f75799030", # v1.1.3 Sep 28, 2018 (LATEST OFFICIAL VERSION)
    remote = "https://github.com/gorilla/sessions.git",
)

new_git_repository(
    name = "go_gorilla_securecookie",
    build_file = "//:third_party/go/gorilla_securecookie.BUILD",
    commit = "e59506cc896acb7f7bf732d4fdf5e25f7ccd8983", # v1.1.1 Feb 24, 2017 (LATEST OFFICIAL VERSION)
    remote = "https://github.com/gorilla/securecookie.git",
)

new_git_repository(
    name = "go_gorilla_context",
    build_file = "//:third_party/go/gorilla_context.BUILD",
    commit = "8559d4a6b87e4f517ec1846eb90a192b8748cc89", # Jun 27, 2019 (LATEST OFFICIAL VERSION)
    remote = "https://github.com/gorilla/context.git",
)

new_git_repository(
    name = "go_gorilla_csrf",
    build_file = "//:third_party/go/gorilla_csrf.BUILD",
    commit = "9b0e3acb4f79e4bf9415d6144123987e7b8527cb", # Jun 25, 2019 (LATEST GIT COMMIT)
    remote = "https://github.com/gorilla/csrf.git",
)

new_git_repository(
    name = "go_gorilla_mux",
    build_file = "//:third_party/go/gorilla_mux.BUILD",
    commit = "5dd56998c22c824ad2e13c50bc3213e85b125134", # Jun 4, 2016  (UPDATE REQUIRED! above, breaks)
    remote = "https://github.com/gorilla/mux.git",
)

new_git_repository(
    name = "go_pkg_errors",
    build_file = "//:third_party/go/pkg_errors.BUILD",
    commit = "27936f6d90f9c8e1145f11ed52ffffbfdb9e0af7", # Feb 27, 2019 (LATEST GIT COMMIT)
    remote = "https://github.com/pkg/errors.git",
)

new_git_repository(
    name = "go_mandrill",
    build_file = "//:third_party/go/keighl_mandrill.BUILD",
    commit = "1775dd4b3b4121aa2731132552ebcff17253d103", # Jun 5, 2017 (LATEST GIT COMMIT)
    remote = "https://github.com/keighl/mandrill.git",
)

new_git_repository(
    name = "go_logrus",
    build_file = "//:third_party/go/Sirupsen_logrus.BUILD",
    commit = "07a84ee7412e7a28663d92930a1d46f81b124ee1", # Jul 1, 2019 (LATEST GIT COMMIT)
    remote = "https://github.com/Sirupsen/logrus.git",
)

new_git_repository(
    name = "go_testify",
    build_file = "//:third_party/go/stretchr_testify.BUILD",
    commit = "ffdc059bfe9ce6a4e144ba849dbedead332c6053", # v1.3.0 Dec 5, 2018 (LATEST OFFICIAL VERSION)
    remote = "https://github.com/stretchr/testify.git",
)

new_git_repository(
    name = "go_negroni",
    build_file = "//:third_party/go/urfave_negroni.BUILD",
    commit = "c6a59be0ce122566695fbd5e48a77f8f10c8a63a", # v1.0.0 Sep 2, 2018 (LATEST OFFICIAL VERSION)
    remote = "https://github.com/urfave/negroni.git",
)

new_git_repository(
    name = "go_assetfs",
    build_file = "//:third_party/go/elazarl_assetfs.BUILD",
    commit = "38087fe4dafb822e541b3f7955075cc1c30bd294", # Feb 23, 2018 (LATEST GIT COMMIT)
    remote = "https://github.com/elazarl/go-bindata-assetfs.git",
)

new_git_repository(
    name = "go_raven",
    build_file = "//:third_party/go/getsentry_raven.BUILD",
    commit = "5c24d5110e0e198d9ae16f1f3465366085001d92", # Jun 19, 2019 (LATEST GIT COMMIT)
    remote = "https://github.com/getsentry/raven-go.git",
)

new_git_repository(
    name = "go_grpc",
    build_file = "//:third_party/go/google_grpc.BUILD",
    commit = "73b304d882a0822aaeb3c982c747563777e79586", # Jun 28, 2019 (LATEST GIT COMMIT)
    remote = "https://github.com/grpc/grpc-go.git",
)

new_git_repository(
    name = "go_genproto",
    build_file = "//:third_party/go/google_genproto.BUILD",
    commit = "eb59cef1c072c61ea4f7623910448d5e9c6a4455", # Jun 27, 2019 (LATEST GIT COMMIT)
    remote = "https://github.com/googleapis/go-genproto.git"
)

## slight bug, BUILD.bazel messing up the build. After build fails need to remove these files:
## rm -rf /home/vagrant/.cache/bazel/_bazel_vagrant/1234567890/external/go_grpc_gateway/utilities/BUILD.bazel && rm -rf /home/vagrant/.cache/bazel/_bazel_vagrant/1234567890/external/go_grpc_gateway/runtime/BUILD.bazel && rm -rf ~/.cache/bazel/_bazel_vagrant/1234567890/external/go_grpc_gateway/internal/BUILD.bazel
## third_party/googleapis/google/api missing .go files, need to generate from .proto. CMD: 
##  1. protoc --go_out=. google/api/http.proto
##  2. protoc --go_out=. google/api/annotations.proto
## need to find a way to make it neatly via BUILD.bazel
new_git_repository(
    name = "go_grpc_gateway",
    build_file = "//:third_party/go/grpc_gateway.BUILD",
    commit = "740ef2ee80c49ed4a272e8c3b54ebf352109f572", # Jun 26, 2019 (LATEST GIT COMMIT)
    remote = "https://github.com/grpc-ecosystem/grpc-gateway.git",
)

new_git_repository(
    name = "go_gogo_protobuf",
    build_file = "//:third_party/go/gogo_protobuf.BUILD",
    commit = "dadb625850898f31a8e40e83492f4a7132e520a2", # Jun 11, 2019 (LATEST GIT COMMIT)
    remote = "https://github.com/gogo/protobuf.git",
)

new_git_repository(
    name = "go_glog",
    build_file = "//:third_party/go/glog.BUILD",
    commit = "23def4e6c14b4da8ac2ed8007337bc5eb5007998", # Jan 27, 2016 (LATEST GIT COMMIT)
    remote = "https://github.com/golang/glog.git",
)

new_git_repository(
    name = "go_protobuf",
    build_file = "//:third_party/go/protobuf.BUILD",
    commit = "b285ee9cfc6c881bb20c0d8dc73370ea9b9ec90f", # May 17, 2019 (LATEST GIT COMMIT)
    remote = "https://github.com/golang/protobuf.git",
)

new_git_repository(
    name = "go_certifi",
    build_file = "//:third_party/go/certifi_gocertifi.BUILD",
    commit = "deb3ae2ef2610fde3330947281941c562861188b", # 2018.01.18 - Jan 18, 2018 (LATEST OFFICIAL RELEASE)
    remote = "https://github.com/certifi/gocertifi.git",
)

new_git_repository(
    name = "go_cloud",
    build_file = "//:third_party/go/google_cloud.BUILD",
    commit = "cf81fad90a1a1de334c4fc27e23eb9a4224b627a", # v0.41.0 - Jul 1, 2019 (LATEST OFFICIAL RELEASE)
    remote = "https://github.com/GoogleCloudPlatform/google-cloud-go.git",
)

new_git_repository(
    name = "go_intercom",
    build_file = "//:third_party/go/intercom.BUILD",
    commit = "1dbafb072bcdb981cad04ad4a0e6e29afbfc0c42", # Mar 19, 2019  (LATEST GIT COMMIT)
    remote = "https://github.com/intercom/intercom-go.git"
)

new_git_repository(
    name = "go_querystring",
    build_file = "//:third_party/go/google_querystring.BUILD",
    commit = "c8c88dbee036db4e4808d1f2ec8c2e15e11c3f80", # Mar 18, 2019 (LATEST GIT COMMIT)
    remote = "https://github.com/google/go-querystring.git",
)

new_git_repository(
    name = "go_google_api",
    build_file = "//:third_party/go/google_api.BUILD",
    commit = "cad4a65739ec9027249a05eec449fe57ff999d48", # Jul 2, 2019 (LATEST GIT COMMIT)
    remote = "https://github.com/google/google-api-go-client.git",
)

new_git_repository(
    name = "go_appengine",
    build_file = "//:third_party/go/golang_appengine.BUILD",
    commit = "9d8544a6b2c7df9cff240fcf92d7b2f59bc13416", # Oct 31, 2017 (UPDATE REQUIRED! above, breaks)
    remote = "https://github.com/golang/appengine.git",
)

new_git_repository(
    name = "go_gorp",
    build_file = "//:third_party/go/gorp.BUILD",
    commit = "f3677d4a0a8838c846ed41bf41927f2c8713bd60", # Nov 4, 2018 (LATEST GIT COMMIT)
    remote = "https://github.com/go-gorp/gorp.git",
)

new_git_repository(
    name = "go_blackfriday",
    build_file = "//:third_party/go/russross_blackfriday.BUILD",
    commit = "a925a152c144ea7de0f451eaf2f7db9e52fa005a", # Jun 17, 2019  (LATEST GIT COMMIT)
    remote = "https://github.com/russross/blackfriday.git",
)

new_git_repository(
    name = "go_sanitized_anchor_name",
    build_file = "//:third_party/go/shurcool_sanitized_anchor_name.BUILD",
    commit = "7bfe4c7ecddb3666a94b053b422cdd8f5aaa3615", # Dec 26, 2018  (LATEST GIT COMMIT)
    remote = "https://github.com/shurcool/sanitized_anchor_name.git",
)

new_git_repository(
    name = "go_structs",
    build_file = "//:third_party/go/fatih_structs.BUILD",
    commit = "878a968ab22548362a09bdb3322f98b00f470d46", # Oct 11, 2018  (LATEST GIT COMMIT)
    remote = "https://github.com/fatih/structs.git",
)

new_git_repository(
    name = "go_mysql",
    build_file = "//:third_party/go/mysql.BUILD",
    commit = "382e13d099fcf5f5994290892ab258fbebbdc5e3", # May 12, 2017 (UPDATE REQUIRED! above, breaks)
    remote = "https://github.com/go-sql-driver/mysql.git",
)

new_git_repository(
    name = "go_x_net",
    build_file = "//:third_party/go/x_net.BUILD",
    commit = "da137c7871d730100384dbcf36e6f8fa493aef5b", # Jun 28, 2019 (LATEST GIT COMMIT)
    remote = "https://github.com/golang/net.git"
)

new_git_repository(
    name = "go_x_oauth2",
    build_file = "//:third_party/go/x_oauth2.BUILD",
    commit = "0f29369cfe4552d0e4bcddc57cc75f4d7e672a33", # 
    remote = "https://github.com/golang/oauth2.git"
)

new_git_repository(
    name = "go_x_time",
    build_file = "//:third_party/go/x_time.BUILD",
    commit = "9d24e82272b4f38b78bc8cff74fa936d31ccd8ef", # Feb 16, 2019  (LATEST GIT COMMIT)
    remote = "https://github.com/golang/time.git"
)

new_git_repository(
    name = "go_x_crypto",
    build_file = "//:third_party/go/x_crypto.BUILD",
    commit = "cc06ce4a13d484c0101a9e92913248488a75786d", # Jun 21, 2019  (LATEST GIT COMMIT)
    remote = "https://github.com/golang/crypto.git"
)

new_git_repository(
    name = "go_x_text",
    build_file = "//:third_party/go/x_text.BUILD",
    commit = "342b2e1fbaa52c93f31447ad2c6abc048c63e475", # Dec 15, 2018 (LATEST GIT COMMIT)
    remote = "https://github.com/golang/text.git"
)

new_git_repository(
    name = "go_x_sync",
    build_file = "//:third_party/go/x_sync.BUILD",
    commit = "112230192c580c3556b8cee6403af37a4fc5f28c", # Apr 23, 2019 (LATEST GIT COMMIT)
    remote = "https://github.com/golang/sync.git"
)

new_git_repository(
    name = "go_opencensus",
    build_file = "//:third_party/go/go_opencensus.BUILD",
    commit = "5897c5ce32247fc8af19c7710abd96e3304fb43c", # Jun 4, 2018 (UPDATE REQUIRED! above, breaks)
    remote = "https://github.com/census-instrumentation/opencensus-go.git"
)

new_git_repository(
    name = "golang_lru",
    build_file = "//:third_party/go/golang_lru.BUILD",
    commit = "59383c442f7d7b190497e9bb8fc17a48d06cd03f", # May 20, 2019 (LATEST GIT COMMIT)
    remote = "https://github.com/hashicorp/golang-lru.git"
)

new_git_repository(
    name = "googleapis_gax",
    build_file = "//:third_party/go/googleapis_gax.BUILD",
    commit = "bd5b16380fd03dc758d11cef74ba2e3bc8b0e8c2", # May 13, 2019 (LATEST GIT COMMIT)
    remote = "https://github.com/googleapis/gax-go.git",
)