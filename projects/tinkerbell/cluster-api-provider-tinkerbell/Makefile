BASE_DIRECTORY:=$(shell git rev-parse --show-toplevel)
GIT_TAG:=$(shell cat GIT_TAG)
GOLANG_VERSION?="1.17"

REPO=cluster-api-provider-tinkerbell
REPO_OWNER=tinkerbell

BASE_IMAGE_NAME?=eks-distro-minimal-base-nonroot


BINARY_TARGET_FILES=manager
SOURCE_PATTERNS=.
EXTRA_GO_LDFLAGS=$(shell $(BUILD_LIB)/version.sh $(REPO) sigs.k8s.io/cluster-api-provider-packet/version)

HAS_S3_ARTIFACTS=true

include $(BASE_DIRECTORY)/Common.mk

s3-artifacts: create-manifests

.PHONY: create-manifests
create-manifests: tarballs
	build/create_manifests.sh $(REPO) $(OUTPUT_DIR) $(ARTIFACTS_PATH) $(GIT_TAG) $(IMAGE_REPO) $(IMAGE_TAG)


########### DO NOT EDIT #############################
# To update call: make add-generated-help-block
# This is added to help document dynamic targets and support shell autocompletion
# Run make help for a formatted help block with all targets
include Help.mk
########### END GENERATED ###########################
