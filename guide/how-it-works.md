# How the Engine works

## TLDR;

The MysteryMaker is a tool to create, edit, debug and export the engine's project files in the zip format. Then the Velius Engine, that is built wthin the [Godot Game Engine](https://godotengine.org), comes in. It processes the project file and gives instructions to the in the project file contained theme. The theme finally determines what the player sees and how to interact with it.

## How MysteryMaker works

MysteryMaker (MM) was built using Windows Forms and C#. The program enables the user to develop MM projects. A MM project consists of a directory,  containing a Project.json and a theme folder. The Project.json has all your projects information including all the dialogues and scripts. The theme folder contains - obviously - the theme of the project. Having a theme installed is necessary to debug the project.

## How themes work

Themes are single, uncompiled Godot projects. They use the "Velius Development Toolkit" addon as an API to comunicate with the client's backend. Creating a theme is an *easy* and creative process. Basically you just create a Game in the [Godot Game Engine](https://godotengine.org). Then you define what to do with things like the dialogues', script's or user's data.

::: tip
Creating your own theme may give you infinite possibilities, but also consumes a lot of time. So downloading official or community made themes from the market place will be the easiest and most common way for telling your story.
:::

## How the client works

// TODO

## How the docs work

// TODO

## How the market place works

// TODO
