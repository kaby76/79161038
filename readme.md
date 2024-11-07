# Stackoverflow question 79161038

This repo contains two grammars, an original as posted in
the question https://stackoverflow.com/questions/79161038/antlr4-where-is-the-ambiguity,
the other one with a subset. Although both start with the same start rule and
never call any of the productions that were deleted in the second grammar,
the grammar with the rules performs worse because of "full context fallback".

To see how this works, build both by running `dotnet build`, then `./bin/Debug/net8.0/Test.exe -d -trace in'.
The difference are the lines
```
https://stackoverflow.com/questions/79161038/antlr4-where-is-the-ambiguity?noredirect=1#comment139600048_79161038
ReportContextSensitivity d=11 (explicitEvaluationString), input=' '
```

The meaning is clear: full context parsing may be required depending on unrelanted rules.
