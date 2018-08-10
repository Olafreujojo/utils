# XML toolbox
- [XML toolbox](#xml-toolbox)
    - [Validate xml against xsd](#validate-xml-against-xsd)
    - [xpath](#xpath)

## Validate xml against xsd
```
xmllint --noout --schema schema.xsd file.xml
```

## xpath
```
xmllint --xpath '/path/to/tag[predicate]/@attribute'
```

count
```
xmllint --xpath 'count(/path/to/tag[predicate or otherpredicate])'
```

Value only
```
xmllint --xpath 'string(/path/to/tag[predicate]/@attribute)'
```

