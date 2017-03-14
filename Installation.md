## This document is out of date

 * TODO: Update to reference Argon, and include the following update to the invocation:
```bash
noflo-nodejs --register false --ide http://localhost:8080/ --secret secret --graph output.json --save-graph output.json
noflo-ui --secret secret --host localhost --port 8080 --websocket ws://localhost:3569
```

# Installation

The RDF Pipeline Framework is layered on node.js 4.2.2 and noflo. So you need to install each in turn and then finally link up the RDF Pipeline Framework components.

The RDF Pipeline Framework has only been tested on Linux platforms: Centos 7.1, Ubuntu 14.04 and Ubuntu 16.04.

This sequence of steps installs the noflo version of the RDF Pipeline Framework on your local Linux computer. 

## 1. (Optional) Install a VM.
Optionally, install Centos 7.1 or Ubuntu 16.04 as virtual machine. Make your network device "bridged" so you can ssh into the virtual machine.

## 2. Install java jdk
Java is only used by some pipelines, but if the JDK isn't installed then later attempts to run ```npm install``` will fail.  See [issue 74](https://github.com/rdf-pipeline/noflo-rdf-pipeline/issues/74).  These commands worked on CENTOS 7:

```bash
sudo yum install java-1.7.0-openjdk
sudo yum install java-devel
```

## 2. Install nodejs 4.2.2 and nvm
You can install nodejs 4.2.2 using either [nvm](http://nvm.sh) or the platform package manager. Nvm has the benefit that it will let you specify a particular version but it's a little more involved to use.

a. Install nodejs:

```bash
cd ~
# If nodejs was previously installed, you might need to do:
sudo yum erase nodejs
# Then do:
sudo yum install nodejs
```

b. Install and configure nvm:

```bash
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.32.1/install.sh | bash
export NVM_DIR="/home/dbooth/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"  # This loads nvm
nvm install v4.2.2
```
c. Install nodejs v4.2.2:

```bash
nvm install v4.2.2
```

d. Test it:

```bash
$ node --version # report the version
4.2.2

$ node -p -e 'process.cwd()' # run a one-liner
/home/you
```

## 3. Install noflo-ui from the RDF Pipeline Framework
Clone the noflo-ui repository and checkout the develop branch. Follow the instructions in the README.md to install the branch globally via npm link.

    $ cd ~
    $ git clone https://github.com/rdf-pipeline/noflo-ui.git
    $ cd noflo-ui
    $ git checkout develop
    $ npm install
    $ grunt build
    $ npm link

## 4. Install noflo-nodejs from the RDF Pipeline Framework
Clone the noflo-nodejs repository and checkout the develop branch. Follow the instructions in the README.md to install the branch globally via npm link.

    $ cd ~
    $ git clone https://github.com/rdf-pipeline/noflo-nodejs.git
    $ cd noflo-nodejs
    $ git checkout develop
    $ npm install
    $ npm link

## 5. Install noflo-rdf-components from the RDF Pipeline Framework
Clone the noflo-rdf-components repository and checkout the develop branch. Then add the noflo-nodejs to the project.

    $ cd ~
    $ git clone https://github.com/rdf-pipeline/noflo-rdf-components.git
    $ cd noflo-rdf-components
    $ git checkout develop
    $ npm install
    $ npm link noflo-nodejs

## 6. Test your installation

In this section, we'll start the noFlo service to make sure our installation works.  The JavaScript version of the RDF Pipeline Framework uses NoFlo, which is based on node.js.

The simplest graph to run has no nodes and no edges, and therefore doesn't do anything. We use it to test that the NoFlo server and user interface will spin up.
Once you're sure it does, your own graphs will be easier to debug.

A few brief caveats:

1. For these examples, node.js was installed using using the node version manager [nvm](https://www.npmjs.com/package/nvm).  Nvm lets you run multiple versions of node on a single machine so that you can switch between them.  (Currently the RDF Pipeline Framework runs over node 4.2.2, the "long term support" version, as do these examples. )  However, there are other ways to install node.js.  As a consequence, the paths reported below might be different from yours, especially if you've installed node using a package manager like `apt`, `snap`, `yum` or `dnf`.
2. The next set of commands make sure you are running the version of node and the noflo server you expect. You may have to issue slightly different commands for your shell.  The commands below used `bash`.
3. You may want to race ahead immediately. We suggest you don't. NoFlo is powerful, but has several moving parts. Be methodical.
4. NoFlo generally doesn't log to standard error, leaving that to individual components. It's easy, therefore, for something to be misconfigured and fail silently. Our "small steps, bottom up" approach mitigates some of that potential confusion,
especially if you are used to other servers that do the logging.

Since the RDF Pipeline Framework uses the NoFlo server, to begin let's first make sure we can run the NoFlo server with a node.js that we expect:

```bash
$ type -p node  # dude, where's my node? -p reports the path
/home/mcarifio/.nvm/versions/node/v4.2.2/bin/node

$ node --version # yup, that's the version
v4.2.2

$ type -p noflo-ui # dude, where's my noflo-ui?
/home/mcarifio/.nvm/versions/node/v4.2.2/bin/noflo-ui
```

If your shell found the executables you expected and you got versions you expected, let's run an empty NoFlo graph. Run the noflo-ui and noflo-nodejs from the noflo-rdf-components repository:

```bash
cd ~/noflo-rdf-components
noflo-ui --host localhost --port 8080 & sleep 1
echo "{}" > output.json
node node_modules/.bin/noflo-nodejs --register false --host localhost --port 3569 --secret mysecret --ide http://localhost:8080/ --graph output.json --save-graph output.json
```

The UI can now be accessed at [localhost:3569](http://localhost:3569/) and [localhost:3569/node/](http://localhost:3569/node/) . 

**Explanation:**
* Our components are not compatible with the noflo UI code, so they need to be in separate repositories.  
* There are two ports being used, for two servers:  8080 serves the NoFlo GUI to the browser; 3569
node.js is used to run our own server on port 3569, and serves information about the nodes in the currently running pipeline.  For example, by accessing [localhost:3569/node/](http://localhost:3569/node/) you can now see a list of nodes in the current pipeline.  By clicking on one of the nodes listed, you can see detailed information about that node.
* We have modified noflo-ui to redirect 8080/node (or whatever port is specified) to 3569/node .

Now point your web browser at [localhost:3569](http://localhost:3569/). You should see no nodes, no edges and the execution will be finished. It will resemble something like this:

![noflo ui without a graph](images/empty-ui.png)

Next, click on the `default/main` graph (upper left). If you see a long list of components, some prefixed with `RDF-COMPONENTS`, then your installation can find important components and you
can probably create and run graphs. Exit the service above with `control-C`.

So far: NoFlo runs. Now let's run a graph, to be sure that NoFlo can also do that.

## Run Redux

First, we'll create an empty JSON graph `graph/hello.json`.   In a moment we will add to it.

```bash
echo '{}' > graphs/hello.json  # This should not yet exist -- it will be created.
node node_modules/.bin/noflo-nodejs --register false --host localhost --port 3569 --secret mysecret --ide http://localhost:8080/ --graph graphs/hello.json --save-graph graphs/hello.json
```

Second, open [localhost:3569](http://localhost:3569/) in your browser and select the `CORE/Output` component to create a node in the graph.  Specify its `in` port to receive the string literal "Hello, JSON". It should look like this:

![noflo ui without a graph](images/hello-json.png)

Third, having set up the graph, we run it by clicking the green "Run" triangle in the upper right corner. At the command line we see:

```
Hello, JSON!
```

Note that the `CORE/Output` component writes to standard output. In a later exercise, we'll write to the user interface directly.

Finally we exit with `control-C` and find that noflo has saved the modified graph for us in the JSON file:

```bash
cat graphs/hello.json
{
  "properties": {},
  "inports": {},
  "outports": {},
  "groups": [],
  "processes": {
    "core/Output_p4k5c": {
      "component": "core/Output",
      "metadata": {
        "label": "Output",
        "x": 334,
        "y": 100
      }
    }
  },
  "connections": [
    {
      "data": "Hello, JSON!",
      "tgt": {
        "process": "core/Output_p4k5c",
        "port": "in"
      }
    }
  ]
}
```

You can create or edit these JSON graph definitions by hand if you want.  You can also use `.fpb` files (flow-based-programming) instead of JSON, but we will not discuss that format.

After you have installed the parts, you can move on to [Getting Started](Getting-Started-With-the-RDF-Pipeline) to start building pipelines.
