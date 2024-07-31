# Software Requirements Document (SRD) for zSquad

## Table of Contents

-   [1. Introduction](#1-introduction)
    -   [1.1 Purpose](#11-purpose)
    -   [1.2 Scope](#12-scope)
    -   [1.3 Definitions](#13-definitions)
-   [2. Functional Requirements](#2-functional-requirements)
    -   [2.1 Main Menu (UI)](#21-main-menu-ui)
        -   [2.1.1 New Game](#211-new-game)
        -   [2.1.2 Load Game](#212-load-game)
        -   [2.1.3 Options](#213-options)
    -   [2.2 Game Play (CORE)](#22-game-play-core)
        -   [2.2.1 Game State Management](#221-game-state-management)
        -   [2.2.2 Menu Layer](#222-menu-layer)
        -   [2.2.3 Command Layer](#223-command-layer)
        -   [2.2.4 Tactical Layer](#224-tactical-layer)
    -   [2.3 Save/Load System (DB)](#23-saveload-system-db)
        -   [2.3.1 Save Game](#231-save-game)
        -   [2.3.2 Load Game](#232-load-game)
    -   [2.4 Options Menu](#24-options-menu)
        -   [2.4.1 Audio Settings](#241-audio-settings)
        -   [2.4.2 Graphics Settings](#242-graphics-settings)
        -   [2.4.3 Control Settings](#243-control-settings)
-   [3. Non-Functional Requirements](#3-non-functional-requirements)
    -   [3.1 Performance](#31-performance)
    -   [3.2 Usability](#32-usability)
    -   [3.3 Compatibility](#33-compatibility)
    -   [3.4 Reliability](#34-reliability)
    -   [3.5 Security](#35-security)
-   [4. System Architecture](#4-system-architecture)
    -   [4.1 High-Level Architecture](#41-high-level-architecture)
    -   [4.2 Data Management](#42-data-management)
-   [5. User Interface Design](#5-user-interface-design)
    -   [5.1 Main Menu](#51-main-menu)
    -   [5.2 In-Game UI](#52-in-game-ui)
    -   [5.3 Options Menu](#53-options-menu)
-   [6. Development and Testing](#6-development-and-testing)
    -   [6.1 Development](#61-development)
    -   [6.2 Testing](#62-testing)
-   [7. Deployment](#7-deployment)
    -   [7.1 Distribution](#71-distribution)
    -   [7.2 Installation](#72-installation)
-   [8. Documentation](#8-documentation)
    -   [8.1 User Documentation](#81-user-documentation)
    -   [8.2 Developer Documentation](#82-developer-documentation)
-   [9. Glossary](#9-glossary)
-   [10. References](#10-references)

## 1. Introduction

`zSquad` is a 3rd person Isometric single-player game in the vein of games like Xcom and Phoenix
Point. The player takes control of a squad of soldiers as they attempt to meet up with and rejoin
their national command.

### 1.1 Purpose

This document outlines the software requirements for the game `zSquad`. It details the functional
and non-functional requirements needed to guide the development and ensure that the final product
meets needs and expectations.

### 1.2 Scope

`zSquad` is a strategy game designed to provide an engaging experience with multiple gameplay modes,
including a main menu, new game, load game, and options. This document covers the game's
requirements, including user interactions, system behaviors, and constraints.

### 1.3 Definitions

-   **SRD:** Software Requirements Document
-   **Main Menu:** Main menu, New Game, Load Game, Options
-   **Assets:** Art, Audio, Prefabs, Scenes, Scripts, Shaders, Materials, Animations, Resources
-   **End-of-Turn:** End-of-turn actions are actions that, when processed, end a turn prematurely.
    These may or may not be present for reasons of gameplay balance and flow.

## 2. Functional Requirements

-   The game needs to meet numerous goals before it can be called a working demo.
    -   The game must be able to switch from menu state to basebuilding state, to tactical state as
        necessary.
    -   The game must successfully process player turns and enemy turns in a looping manner until
        end of combat.
    -   The game must be able successfully record player interactions during autosave and manual
        saving operations.
    -   The game must be clear of known and obvious game critical bugs.
    -   The game must perform in an efficient manner and meet the specifications most common users
        individual hardware.

### 2.1 Main Menu (UI)

#### 2.1.1 New Game

-   Starts a new game session and loads the initial game scene.

#### 2.1.2 Load Game

-   Allows the user to load a previously saved game.

#### 2.1.3 Options

-   Provides access to settings such as audio volume, graphics quality, and controls.

### 2.2 Game Play (CORE)

#### 2.2.1 Game State Management

-   Manages game states including the Menu, basebuilding, and tactical layers.

#### 2.2.2 Menu Layer

-   The layer where menu operations occur, such as saving and loading; and navigating to the main
    menu, options, or exit game.

#### 2.2.3 Command Layer

-   The layer in which base upgrade, unit upgrade, strategic actions, and mission selection happens.

#### 2.2.4 Tactical Layer

-   The layer where missions take place, from start of combat to end of combat.

### 2.3 Save/Load System (DB)

#### 2.3.1 Save Game

-   Saves the current state of the game to a file.

#### 2.3.2 Load Game

-   Loads a saved game state from a file.

### 2.4 Options Menu

#### 2.4.1 Audio Settings

-   Adjusts music and sound effects volume.

#### 2.4.2 Graphics Settings

-   Adjusts graphics quality and resolution.

#### 2.4.3 Control Settings

-   Customizes key bindings and control schemes.

## 3. Non-Functional Requirements

### 3.1 Performance

-   **3.1.1 Game Performance:** The game should run smoothly on standard hardware with minimal lag
    or delays. Standard hardware for the current version of the game is expected to be: TBD.

### 3.2 Usability

-   **3.2.1 User Interface Usability:** The user interface should be intuitive and easy to navigate.
    Everything should be clearly labeled and naming should make sense considering the context of the
    action taken.
-   **3.2.2 Gameplay Feedback:** The game should provide clear instructions and feedback. This
    includes hover text, displaying appropriate action costs, actions that cause end-of-turn, and
    anything that helps to explain game meta-information to the player.

### 3.3 Compatibility

-   The game should be compatible with Windows 10 and 11 operating systems. Other Windows distros,
    macOS, and Linux are to be considered at a further date.

### 3.4 Reliability

-   The game should handle errors gracefully and provide meaningful error messages. Automated error
    reporting may be considered at a later date.

### 3.5 Security

-   User data and save files should be protected against unauthorized access. The game is intended
    to be a standalone game at release, so further security is deemed unnecessary at this time.

## 4. System Architecture

### 4.1 High-Level Architecture

-   **Frontend:** User interface, game scenes, and interactions.
-   **Backend:** Game logic, save/load systems, and state management.

### 4.2 Data Management

-   **Game Data:** Stored in files and managed by the save/load system. The system will include the
    CORE modules of:
    -   **SaveGame:** Saving games happens here.
    -   **LoadGame:** Loading games happens here.
-   **User Settings:** Managed through configuration files or databases.

## 5. User Interface Design

### 5.1 Main Menu

-   Layout and options for starting a new game, loading a saved game, and accessing settings.

### 5.2 In-Game UI

-   Display of game status, controls, and feedback.

### 5.3 Options Menu

-   Controls for adjusting audio, graphics, and game controls.

## 6. Development and Testing

### 6.1 Development

-   Follow coding standards and best practices for C# and Unity and overall game design.
-   Use version control for source code management.

### 6.2 Testing

-   Perform unit testing, integration testing, and user acceptance testing.

## 7. Deployment

### 7.1 Distribution

-   The game will be distributed through digital platforms only. Speculative distribution platforms
    are itch.io, Steam, and Epic Games.

### 7.2 Installation

-   Provide clear instructions for installing and running the game.

## 8. Documentation

### 8.1 User Documentation

-   Guides and instructions for playing the game and using its features.

### 8.2 Developer Documentation

-   Technical documentation for maintaining and extending the game.

## 9. Glossary

-   **Gameplay:** The interactive experience provided by the game.
-   **UI (User Interface):** The graphical layout and elements used for user interaction.

## 10. References

-   References to any documents, tools, or external resources used in the development of the game.
