# docker-android-build
Building Android Applications in Docker Container

## Create volume to mount local path in container, an name it e.g. "android-build-volume"
docker create -v $(pwd):/app --name android-build-volume android-build

## Check if correct path is available in container
docker run --rm --volumes-from android-build-volume  --workdir="/app" android-build ls -la

#ä Alternatively you can just add the volumes to the run command:

docker run --rm -v ~/.m2:/root/.m2 -v $(pwd)/../mydockergradle:/root/.gradle -v $(pwd):/app --workdir="/app" android-build ./gradlew clean assemble
