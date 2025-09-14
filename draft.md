notes:

checkpointing happens at kubelet level.

checkpoints get saved in a predefined directory.

buildah can be used to create an image from the .tar checkpoint

the image can be uploaded to a registry (don't yet know how this would work with signed images)

the image can be used to create a new pod from the checkpoint

ideas on how to make this work in a user friendly manner in kubernetes:

1) Create a mutating webhook

... gotta go I'll continue these notes later
