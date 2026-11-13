# Adhkar App

A small web app for reading morning and evening adhkar, built with Svelte 5.

## Features

- Choose between morning and evening adhkar
- One dhikr at a time with Arabic text, transliteration and translation
- Tap counter that advances to the next dhikr automatically
- Progress bar
- Previous and next navigation

## Tech

- Svelte 5 (runes: `$state`, `$derived`, `$props`)
- Component-based structure (`DhikrCard`, `ProgressBar`)
- Scoped styles and transitions

## Running locally

    npm install
    npm run dev

## Sources

The adhkar texts are taken from sunnah.com . Each dhikr includes a reference.

## Status

Small demo project. Not a complete adhkar collection.

## Demo

(https://adhkar-app-demo.netlify.app/)
