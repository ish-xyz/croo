notes:

checkpointing happens at kubelet level.

checkpoints get saved in a predefined directory.

buildah can be used to create an image from the .tar checkpoint

the image can be uploaded to a registry (don't yet know how this would work with signed images)

the image can be used to create a new pod from the checkpoint

ideas on how to make this work in a user friendly manner in kubernetes:

1) Create a mutating webhook that will grab an annotation "croo.kubernetes.io/last-checkpoint: $checkpoint-ts" and change the image tag with the last checkpoint.
2) An operator that will look at all pods with annotation "croo.kubernetes.io/checkpoints: 1/5/10/15m"
  a) The operator will process the snapshots and add the timestamp to the annotation in step (1) and the original tag/image address in an annotation croo.kubernetes.io/original-i
mage: $string.
  b) The operator will be in charge of detecting snapshots and taking care of updating annotations.
  c) The operator will also expose APIs
3) The registry daemonset: every node will have a registry. The registry has to passthrough
4) The checkpointer daemonset: this daemonset will be in charge of preparing checkpoints and distributing them to the registries (depending on how many copies are needed/wanted).

gotta go again... will continue later.



