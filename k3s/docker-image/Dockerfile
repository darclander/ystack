FROM rancher/k3s:v1.20.5-k3s1@sha256:01f2f181db87002f1665b2c218c7d0ed2aba1026246657c7dd6f7527702987c1

COPY k3s/docker-image/registries.yaml /etc/rancher/k3s/registries.yaml
# The clusterIP should be predefined
RUN sed -i 's|http://builds-registry.ystack.svc.cluster.local|http://10.43.0.50|' /etc/rancher/k3s/registries.yaml
RUN sed -i 's|http://prod-registry.ystack.svc.cluster.local|http://10.43.0.51|' /etc/rancher/k3s/registries.yaml

# Unfortunately /var/lib/rancher/k3s is a VOLUME so this has no effect on server start
# COPY registry/generic /etc/ystack/registry/generic
# COPY k3s /etc/ystack/k3s
# RUN set -ex; \
#   mkdir -p /var/lib/rancher/k3s/server/manifests; \
#   for base in 00-ystack-namespace in-docker-builds-registry; do \
#     kubectl kustomize /etc/ystack/k3s/$base > /var/lib/rancher/k3s/server/manifests/ystack-$base.yaml; \
#   done
