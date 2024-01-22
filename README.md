# FirstFlatpak
First Flatpak tutorial to learn Flatpak building.

## Steps for building the RPMs/SRPMs yourself
1) Install the following packages (With whatever package manager you use, dnf is used here)
```console
dnf install flatpak flatpak-builder
```
2) Install the platform this Flatpak will be using
```console
flatpak install flathub org.freedesktop.Platform//23.08 org.freedesktop.Sdk//23.08
```
3) Git clone this github
```console
git clone https://github.com/ChrisHobday/FirstFlatpak
```
or Download ZIP with the green button and extract it

4) Build the Flatpak with flatpak-builder (Run this from within the FirstFlatpak directory. Make sure build-dir is removed. This will use the yml manifest to make the Flatpak in the created build-dir.)
```console
flatpak-builder build-dir org.flatpak.Hello.yml
```

## Steps for Installing/Running the built Flatpak
1) Install the built Flatpak (This will install the Flatpak on your system for the current user.)
```console
flatpak-builder --user --install --force-clean build-dir org.flatpak.Hello.yml
```
2) Check that the Flatpak is listed (It should show up as "Hello org.flatpak.Hello".)
```console
flatpak list | grep "Hello"
```
3) Run the installed Flatpak (It should output "Hello world, from a sandbox" to the console.)
```console
flatpak run org.flatpak.Hello
```

## Steps for Uninstalling/Removing the Flatpak
1) Remove the installed Flatpak
```console
flatpak remove org.flatpak.Hello
```
2) Check that the Flatpak is NOT listed (It should no longer show up.)
```console
flatpak list | grep "Hello"
```
