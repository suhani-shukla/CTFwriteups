# substitution2

## Challenge
Crypto challenge — third message in the substitution series. This time punctuation has been stripped out entirely, making a straight frequency attack harder.

## Hints
1. Try refining your frequency attack — maybe analyzing groups of letters would improve your results.

## Solution
Downloaded the message:

```
nafyffoxenefufytpqnafymfppfentkpxeafbaxraezaqqpzqgswnfyefzwyxnhzqgsfnxnxqlefntkpxeafbxlzpwbxlrzhkfystnyxqntlbwezhkfyzatppflrfnafefzqgsfnxnxqlevqzwesyxgtyxphqlehenfgetbgxlxenytnxqlvwlbtgflntpemaxzatyfufyhwefvwptlbgtycfntkpfecxppeaqmfufymfkfpxfufnafsyqsfyswysqefqvtaxraezaqqpzqgswnfyefzwyxnhzqgsfnxnxqlxelqnqlphnqnftzautpwtkpfecxppekwntpeqnqrfnenwbflnexlnfyfenfbxltlbfozxnfbtkqwnzqgswnfyezxflzfbfvflexufzqgsfnxnxqletyfqvnflntafeuxphufyxpfrxlfsxiwfvnfyfefzquwlnfyfbxlbfvflesfzqgswnfyefzwyxnhxenafyfvqyftkfnnfyufaxzpfvqynfzafutlrfpxegnqenwbflnexltgfyxztlaxraezaqqpevwynafymfkfpxfufnatntlwlbfyentlbxlrqvqvvflesxufnfzalxiwfefeeflnxtpvqygqwlnxlrtlfvvfznxufbfvfleftlbnatnnafnqqpetlbzqlvxrwytnxqlvqzweflzqwlnfyfbxlbfvflesfzqgswnfyefzwyxnhnqsxiwfnafxyzwyxqexnhgqnxutnxlrnafgnqtznxufphtenftzaxlrnafgnqtznxufphnaxlcpxcftltnntzcfysxzqznvxetlqvvflesfzwyxnhqyxflnfbaxraezaqqpzqgswnfyefzwyxnhzqgsfnxnxqlnatneffcenqrflfytnfxlnfyfenxlzqgswnfyezxflzftgqlraxraezaqqpfyenftzaxlrnafgnqmxlrtlbfltkpxlrnafgnqbfffybnafxygtzaxlfenafvptrxesxzqZNV{L6Y4G_4L41H515_15_73D10U5_8E1BF808}
```

No spaces or punctuation this time, so the usual word-boundary tricks are out. Ran a `*` through the ciphertext too — it stands in for a missing/unused letter, which is itself a signal for a frequency attack: a normal-English letter frequency table won't have a gap like that, so it narrows down which plaintext letter got dropped from the ciphertext alphabet.

Followed the hint and moved past single-letter frequency into digraph/bigram analysis — common English pairs (`TH`, `HE`, `IN`, `ER`, etc.) show up with predictable relative frequency, which helps disambiguate letters that have similar solo frequencies. TODO: exact tool/script used for the bigram frequency breakdown wasn't captured in the notes.

Anchored the mapping the same way as before — matched the ciphertext's `ZNV{` against the expected `PICOCTF{` wrapper, giving `Z→P`, `N→I`, `V→C` immediately, then extended the substitution alphabet outward from there using the bigram frequency results until the rest of the message resolved to clean English:

```
THEREE*ISTSE*ERALOTHER*ELLESTABLISHEDHIGHSCHOOLCOMPUTERSECURITYCOMPETITIONSINCLUDINGCYBERPATRIOTANDUSCYBERCHALLENGETHESECOMPETITIONSFOCUSPRIMARILYONSYSTEMSADMINISTRATIONFUNDAMENTALS*HICHARE*ERYUSEFULANDMAR*ETABLES*ILLSHO*E*ER*EBELIE*ETHEPROPERPURPOSEOFAHIGHSCHOOLCOMPUTERSECURITYCOMPETITIONISNOTONLYTOTEACH*ALUABLES*ILLSBUTALSOTOGETSTUDENTSINTERESTEDINANDE*CITEDABOUTCOMPUTERSCIENCEDEFENSI*ECOMPETITIONSAREOFTENLABORIOUSAFFAIRSANDCOMEDO*NTORUNNINGCHEC*LISTSANDE*ECUTINGCONFIGSCRIPTSOFFENSEONTHEOTHERHANDISHEA*ILYFOCUSEDONE*PLORATIONANDIMPRO*ISATIONANDOFTENHASELEMENTSOFPLAY*EBELIE*EACOMPETITIONTOUCHINGONTHEOFFENSI*EELEMENTSOFCOMPUTERSECURITYISTHEREFOREABETTER*EHICLEFORTECHE*ANGELISMTOSTUDENTSINAMERICANHIGHSCHOOLSFURTHER*EBELIE*ETHATANUNDERSTANDINGOFOFFENSI*ETECHNI*UESISESSENTIALFORMOUNTINGANEFFECTI*EDEFENSEANDTHATTHETOOLSANDCONFIGURATIONFOCUSENCOUNTEREDINDEFENSI*ECOMPETITIONSDOESNOTLEADSTUDENTSTO*NO*THEIRENEMYASEFFECTI*ELYASTEACHINGTHEMTOACTI*ELYTHIN*LI*EANATTAC*ERPICOCTFISANOFFENSI*ELYORIENTEDHIGHSCHOOLCOMPUTERSECURITYCOMPETITIONTHATSEE*STOGENERATEINTERESTINCOMPUTERSCIENCEAMONGHIGHSCHOOLERSTEACHINGTHEMENOUGHABOUTCOMPUTERSECURITYTOPI*UETHEIRCURIOSITYMOTI*ATINGTHEMTOE*PLOREONTHEIRO*NANDENABLINGTHEMTOBETTERDEFENDTHEIRMACHINESTHEFLAGISPICOCTF{N6R4M_4N41Y515_15_73D10U5_8E1BF808}
```

The `*` turned out to be standing in for `W` throughout — matches the missing letter from the frequency gap noted earlier.

## Flag
```
PICOCTF{N6R4M_4N41Y515_15_73D10U5_8E1BF808}
```