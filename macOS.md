# macOS

## afconvert
### convert audio file
#### from flac to m4a(acc)
`afconvert -f m4af -d acc foo.flac foo.m4a`
#### multiple files
`for i in *flac; afconvert -f m4af -d acc "$i" "${i$.flac}.m4a"`
