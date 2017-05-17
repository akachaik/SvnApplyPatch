# SvnApplyPatch

This repo contains sample for how to programmatically apply patch

Inspired by this repo
https://github.com/JanX2/google-diff-match-patch-git-svn

## Patch To Text

            var file1 = System.IO.File.ReadAllText(@"C:\SomePath\file1.txt");
            var file2 = System.IO.File.ReadAllText(@"C:\SomePath\file2.txt");

            var dmp = new diff_match_patchTest();

            var diffs = dmp.diff_main(file1, file2);

            var sourceText = dmp.diff_text1(diffs);
            var targetText = dmp.diff_text2(diffs);
            var patchs = dmp.patch_make(diffs);
            var patchText = dmp.patch_toText(patchs);

## Patch To Text (Without Diffs)

            var file1 = System.IO.File.ReadAllText(@"C:\SomePath\file1.txt");
            var file2 = System.IO.File.ReadAllText(@"C:\SomePath\file2.txt");
            
            var dmp = new diff_match_patchTest();

            var patchs = dmp.patch_make(file1, file2);
            var patchText = dmp.patch_toText(patchs);
            
## Patch Apply

            var patchContent = System.IO.File.ReadAllText(@"C:\SomePath\patch.txt");
            var file1 = System.IO.File.ReadAllText(@"C:\SomePath\file1.txt");
            
            var dmp = new diff_match_patchTest();
            
            var patchs = dmp.patch_fromText(patchContent);
            var result = dmp.patch_apply(patchs, file1);

            var resultText = result[0].ToString();
