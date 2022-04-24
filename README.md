# lab07


![Jokes Card](https://readme-jokes.vercel.app/api)

Status of Last Build:<br>
<img src="https://github.com/Kyala16/lab07/workflows/Bin/badge.svg?branch=main"><br>

```
#-------------------------------------
#  Lab07 - Work this GitHub Actions
#  @Kyala16
#-------------------------------------

name: ZIP_ARC

on:
  push:
    branches: 
    - main

  workflow_dispatch:

jobs:
  Package_files_ZIP:
    runs-on: ubuntu-latest
    
    steps:
      - uses: actions/checkout@v2
      
      - name: prepare environment
        run: sudo apt install git
      
      - name: Build Zip And Tar
        shell: bash
        run: |
          mkdir build && cd build
          cmake -DGenerator=ARC ..
          cmake --build .
          cpack -G ZIP  
          
      - name: Release
        id: create_release
        uses: actions/create-release@v1
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }} 
        with:
          tag_name: v1.0.0
          release_name: Release v1.0.0
          draft: false
          prerelease: false
          
      - name: Upload Release Asset
        id: upload-release-asset
        uses: actions/upload-release-asset@v1
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        with:
          upload_url: ${{ steps.create_release.outputs.upload_url }}
          asset_path: build/Hello-world-1.0.0-Linux.zip
          asset_name: Solver.zip
          asset_content_type: application/zip
```
