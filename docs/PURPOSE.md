# Purpose

This document explains why the skill exists and what it gives you as a developer. If you read only two files, read this and the README.

## The problem

The real state of an application lives in its database: the tables and their columns, how they relate, which values are allowed, who can read and write what, and the views and functions the application exposes. Yet that truth is hard to see. It is usually spread across a large database dump and a long history of migration files, and the reasons behind the design are not written down anywhere. To answer a simple question, such as which rows a user can read, you end up reading migrations and security rules by hand and assembling the answer yourself.

This is hardest for the people who most need clarity: developers new to the project, and developers who are still learning how databases work.

## What it gives you

A clear picture of the whole database that you can read like a document. The skill writes the current structure, the security rules, and the exposed views and functions into plain files in the repository, so you can open them, search them, and follow them without special tools.

The reasons behind the design, kept next to the data. The skill encourages capturing the intent of a decision as a short comment on the database object itself, so the next person reads not only the shape of a column but why it is that shape.

The ability to work without the database. Because the picture is committed to the repository, you can read and review it with no running database and no credentials. You can share a single file with a teammate or hand it to an AI assistant.

Confidence that the picture is current. The files are generated from the live database and regenerated as it changes, so they reflect reality rather than someone's memory, and each change shows up as a clean diff over time.

Safety while you learn. The skill only reads your database, and it asks before anything that could affect your data, so exploring is never dangerous.

## If you are new

When you join a project, you can understand its data layer by reading one folder instead of reverse-engineering migrations. You can ask the database questions by opening a file or searching for a name. You can see the security rules and relationships before you change anything, so you are far less likely to break something you did not understand. And when a design looks surprising, the comment next to it often tells you why, instead of leaving you to guess.

## For the team

The same picture captures knowledge that usually leaves when a person does, makes schema changes reviewable as diffs, and gives everyone, human or AI, the same shared understanding to reason from. Over time the repository accumulates a readable, trustworthy history of how the data layer evolved and why.

## The bigger goal

The aim is to make the data layer easy for both people and AI agents to work with, and safe for newcomers to operate on. The database becomes a single source of truth for its data and the intent behind its shape, readable and shareable by anyone, so that decisions about it are made with understanding rather than guesswork.
