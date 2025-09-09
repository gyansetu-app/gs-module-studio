# GyanSetu Module Studio

A platform for educators to create content modules for GyanSetu!

## What is a module?

A module is a bundle of various components including static files, images, short videos and dynamic web content which that may contain:

- Mini-games
- Quizzes
- 3D Models
- Flashcards
- DIKSHA Content
- AR/VR Simulations

that all pertain to a specific chapter of the student's course.

The problem statement emphasized on the fact that this would be a project that caters to rural India where internet connectivity is limited and interrupted. Having the content split into modules of smaller sizes fixes this problem as these can be dynamically downloaded and offloaded depending on internet connectivity and phone storage.

## The Content Modules spec

Content Modules are self-contained packages that extend the main app with additional functionality, interactive content, or media. Each module may include mini games, quizzes, flashcards, 3D/VR assets, PDFs, and other educational or entertainment content.

### 1. Structure

Each Module should follow this scaffolding structure:

```ruby
my-module/
 ├─ module.json          # Metadata and module configuration
 ├─ frontend.js          # Mini game or React component entrypoint
 ├─ backend.js           # Backend logic entrypoint
 ├─ quiz.json            # Quiz metadata
 ├─ flashcards.json      # Flashcard metadata
 ├─ assets/              # Images, videos, 3D models, PDFs, etc.
 └─ README.md            # Module-specific documentation
```

### 2. `module.json` (Required)

This defines the basic information and entrypoints for the module

```json
{
  "id": "biology101",
  "version": "1.0.0",
  "type": ["quiz", "flashcards", "minigame"],
  "title": "Intro to Biology",
  "author": "Your Name",
  "description": "A module introducing basic biology concepts with quizzes and interactive games.",
  "entrypoints": {
    "frontend": "./frontend.js",
    "backend": "./backend.js",
    "quiz": "./quiz.json",
    "flashcards": "./flashcards.json"
  },
  "assets": ["assets/cell.png", "assets/mitosis.mp4", "assets/3d-model.glb"]
}
```

- `id` must be unique across all modules.
- `type` indicates which content the module contains.
- `entrypoints` map each type of content to its corresponding file.

### 3. Mini Games

- Mini Games should be shipped as **ES Modules** exporting a react component or an initialization function.

```js
import React from "react";

export default function MiniGame({ containerId }) {
  return (
    <div id={containerId} className="w-full h-full">
      Game Content
    </div>
  );
}
```
