# keda-migration-testenv

ArgoCD-managed KEDA `ScaledObject`s for a Kafka autoscaling test environment on
eks-test-ph. The `scaledobjects/` directory is synced by an ArgoCD Application
(automated + self-heal), so these objects carry `argocd.argoproj.io/tracking-id`
and are recreated if deleted — a GitOps-managed autoscaling policy.

Two consumers (`orders` and `analytics` namespaces) scale 1–5 on Kafka consumer
lag. The Kafka broker, consumers, and load producer are deployed separately as
the workloads; this repo holds only the autoscaling policy.
