# iPOP-UP HPC Cluster introduction
## Index

## What is an High Performance Computing Cluster

### How does a classic computer work and why use an HPC Cluster ?
A classic computer has several types of components :

- One or more CPU (Central Processing Unit) : A CPU is the element responsible for executing the most basic instructions requested by most softwares. You may also have heard the term microprocessor, which corresponds to the physical chip, however, a single microprocessor can contain several CPUs.
- RAM (Random Access Memory) : Is the space where data is stored short term, it is used to temporarily store the data while it is being processed
- Storage Space : The storage space is used to keep big amounts of data in a more permanent way
- GPU (Graphical Processing Unit) : a GPU is an element specialised in modifying the RAM, it mostly used to deal with display, but can also be used in several types of specialised computation, such as deep learning training or several proteomics studies.

A personnal computer has enough ressources to run several tasks, such as browsing internet, edit a text document or a spreadsheet, some computers are even build for some specific tasks such as playing high-end video-games.

However, several tasks are so ressource intensive that they ask for more ressources than that, for those, we use an HPC Cluster. An HPC cluster can be viewed as several big computers, called nodes, connected together, in a way that can make them work together similarly as a classic system would. These nodes are stored in a specific room with a specific infrastructure thant can handle the presence of so many computers in the same room, and keep them in working order.

Which means, that you will only access this cluster from a distance, notably from SSH accessible

## SSH Access
You will first need a cluster account, which will be provided on demand.

Then, to access the cluster via SSH, open a terminal on your device and connect in the following way
```{shell}
ssh accountName@ipop-up.rpbs.univ-paris-diderot.fr
```
If it is the first time you are connecting on this device, you might have to confirm your intent, then your password will be asked, type it and press enter

You will then be connected to the HPC Cluster "Login node" in your `home` directory. This node is only to be used for very small operations (`cd`, `ls`, `mv`, `mkdir` ...)

## The SLURM workload manager
If this login node is only to do some very light operations, how to run demanding programs ? For that, we're going to use SLURM.

SLURM is the program which manages the repartition of computational ressources between users. It makes sure that everyone has the memory, and CPU time necessary to run their job, as well as making sure that no one person is hoarding all the ressource. To explain a bit how it works, we'll have to go over some vocabulary.
- Account : A logical group of users
- Ressources : a catch all term including CPU time, RAM and others
- Partitions : Logical (possibly overlapping) sets of nodes

We will walk you through some examples of how to use SLURM in practice while explaining how this works, for a more formal presentation, we encourage you to go and read SLURM's user [documentation](https://slurm.schedmd.com/quickstart.html)

### An example of a short task
if you were to launch an executable right now, just after an SSH connexion, you would not be using the computing power of the HPC, but only use the login node power (and cluter it). You can see this by running the `hostname` command, which print the name of the system you are currently on

```{bash}
> hostname
ipop-up.rpbs.univ-paris-diderot.fr
```

`ipop-ip.rpbs.unv-paris-diderot.fr` is the name of the login node. In order to ask SLURM to create a job and run this command on an actual computing node, a simple way to do it it to preface it by `srun -p ipop-up`

```{bash}
> srun -p ipop-up hostname
cpu-node130
```

You can see that the command `hostname`has been exported and ran on an actual computing node, (although if you try it, it might run aon a different computing node) and the result has been sent straight into your terminal.

of course `hostname`is not a command asking for a lot of computational power, so let's give a more realistic example. Let's say you want to expand the file `raw_data.tar.gz`, which is quite heavy.

The way to do it would be

```{bash}
srun -p ipop-up tar -xvf raw_data.tar.gz
```

However if you were try this kind of command, you might notice that it will occupy your terminal, making it ill-fitted for more complex computations. So let's run though a more realistic example.

### What about something longer ?




### Todo list on this page

TODO How will the acounts work in the background ?

TODO What are the partitions

TODO detail the actual architecture

TODO Put up to date once we've got some data banks installed

TODO Job arrays

TODO


### (Optional) Create a SSH Key for easier access


## FAQ
