1   git show aefea

    commit aefead2207ef7e2aa5dc81a34aedf0cad4c32545
    
    Update CHANGELOG.md
    
2   git log --oneline 85024d3

    85024d310 (tag: v0.12.23)
    
3   git show b8d720^

    commit 56cd7859e05c36c06b56d013b55a252d0bb7e158
    
    git show b8d720^2
    
    commit 9ea88f22fc6269854151c571162c5bcf958bee2b
    
4   git log v0.12.23..v0.12.24 --oneline

    33ff1c03b (tag: v0.12.24) v0.12.24
    b14b74c49 [Website] vmc provider links
    3f235065b Update CHANGELOG.md
    6ae64e247 registry: Fix panic when server is unreachable
    5c619ca1b website: Remove links to the getting started guide's old location
    06275647e Update CHANGELOG.md
    d5f9411f5 command: Fix bug when using terraform login on Windows
    4b6d06cc5 Update CHANGELOG.md
    dd01a3507 Update CHANGELOG.md
    225466bc3 Cleanup after v0.12.23 release
    
5   git log -S"func providerSource"
    commit 8c928e83589d90a031f811fae52a81be7153e82f
    
6   git grep -n "globalPluginDirs"
    git log --oneline -L:globalPluginDirs:plugins.go
    78b122055
    52dbf9483
    41ab0aef7
    66ebff90c
    8364383c3
    
7   git log -S"synchronizedWriters"
    git show 5ac311e2a91e381e2f52234668b49ba670aa0fe5
    Author: Martin Atkins <mart@degeneration.co.uk>
