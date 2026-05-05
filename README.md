# Getting started with this knowledge base setup

## First, you need Claude Code:

Claude Code is the brain of the operation. It organizes, synthesizes, and produces the content of the knowledge base.

Read how to download here (browser link): https://code.claude.com/docs/en/overview

Or just use cUrl (put into terminal):

curl -fsSL https://claude.ai/install.sh | bash

## Second, you need Obsidian

Obsidian is the user-facing UI of the knowledge base. The human user interacts primarily through Obsidian.

Read how to download here (browser link): https://obsidian.md/

## Lastly, put it all together

Navigate to a place in user space (I'd recommend home dir or documents on Mac) in terminal and run:

git clone "https://github.com/gabrielkern/cc-knowledge-base.git"

This will make a directory called cc-knowledge-base with the base file system laid out.

Then, use "open folder as vault" within Obsidian, selecting this folder you just made.

Drop in any sources into the proper folders with descriptive names, just dump content into the raw/ directory.

Then navigate to the directory you just made, fire up a Claude Code instance, and instruct for an INGEST of the files you made and a QUERY for any questions you want answered about them.

Depending on the project, different raw/ subdirectories may make sense. If you add them, make sure you adjust CLAUDE.md accordingly. That file is the layer of communication between Claude Code and the knowledge base structure you're laying out.