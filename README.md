# Ubuntu WSL for Developers :computer::zap:

## Installation

1. Download ubuntu-wsl-1.0.1.tag.gz from release
2. Unpack it
3. Import tar file

   ```bash
   wsl --import "Ubuntu-WSL-1.0.1" C:\\Users\\rob\\Ubuntu-WSL-1.0.1 .\\ubuntu-wsl-1.0.1.tar
   ```

4. Create WSL Machine

   ```bash
   wsl install -d Ubuntu-WSL-1.0.1
   ```

## Import own image as wsl

1. Build or Pull Image

   ```bash
   docker build --tag ubuntu-wsl:1.0.1 --file Dockerfile .
   ```

   OR

   ```bash
   docker pull ubuntu-wsl:1.0.1
   ```

2. Run image

   ```bash
   docker run --name ubuntu-wsl-1.0.1 -it ubuntu-wsl:1.0.1 bash -C exit
   ```

3. Export container as tar file

   ```bash
   docker export --output ubuntu-wsl-1.0.1.tar ubuntu-wsl-1.0.1
   ```

4. Move tar to windows file system

   ```bash
   mkdir -p /mnt/c/Users/$USER/Ubuntu-WSL-1.0.1 && mv ubuntu-wsl-1.0.1.tar /mnt/c/Users/$USER/
   ```

5. Import tar file

   ```bash
   wsl --import "Ubuntu-WSL-1.0.1" C:\\Users\\rob\\Ubuntu-WSL-1.0.1 .\\ubuntu-wsl-1.0.1.tar
   ```

6. Create WSL Machine

   ```bash
   wsl install -d Ubuntu-WSL-1.0.1
   ```

NOTE: all steps can be done with `podman Desktop`

## Publish image to github registry

1. Login Github Registry

   ```bash
   echo "YOUR_PASSWORD" | docker login ghcr.io --username YOUR_USERNAME --password-stdin
   ```

2. Push Github Registry

   ```bash
   docker tag ubuntu-wsl:1.0.1 ghcr.io/robertonav20/ubuntu-wsl-for-developers/ubuntu-wsl:1.0.1
   docker push ghcr.io/robertonav20/ubuntu-wsl-for-developers/ubuntu-wsl:1.0.1
   ```

3. Login Docker Registry

   ```bash
   echo "YOUR_PASSWORD" | docker login docker.io --username YOUR_USERNAME --password-stdin
   ```

4. Push Docker Registry

   ```bash
   docker tag ubuntu-wsl:1.0.1 docker.io/robnav24241/ubuntu-wsl-for-developers:1.0.1
   docker push docker.io/robnav24241/ubuntu-wsl-for-developers:1.0.1
   ```

## Useful WSL Command

- Show All WSL

  ```bash
      wsl --list --all
  ```

- Import WSL

  ```bash
      wsl --import "Ubuntu-WSL-1.0.1" C:\\Users\\rob\\Ubuntu-WSL-1.0.1 .\\ubuntu-wsl-1.0.1.tar
  ```

- Install WSL

  ```bash
      wsl install -d Ubuntu-WSL-1.0.1
  ```

- Unregister WSL

  ```bash
      wsl --unregister Ubuntu-WSL-1.0.1
  ```

- Shutdown WSL

  ```bash
      wsl --shutdown
  ```

- Mount Windows Path to WSL

  ```bash
      sudo mkdir -p /mnt/share && sudo mount -t drvfs 'YOUR_WINDOWS_PATH' /mnt/share
  ```
