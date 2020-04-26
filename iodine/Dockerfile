from alpine as build
arg commit=8e14f18282dea137f1f4d574f5f52c6bfa2f1c34
run apk add --no-cache gcc make zlib-dev curl unzip linux-headers musl-dev patch
run curl -sSL -o iodine.zip https://github.com/yarrick/iodine/archive/$commit.zip
run unzip -d / iodine.zip
workdir /iodine-$commit
copy nodaemon.patch .
run patch -p1 <nodaemon.patch
run make HEAD_COMMIT=$commit

from alpine
arg commit=8e14f18282dea137f1f4d574f5f52c6bfa2f1c34
copy --from=build /iodine-$commit/bin/iodine /bin/iodine
copy --from=build /iodine-$commit/bin/iodined /bin/iodined
entrypoint ["/bin/iodined", "-f"]
