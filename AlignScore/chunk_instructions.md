# Reassemble Checkpoint Files on Linux

These instructions explain how to reassemble the downloaded `.bin` chunks into their original `.ckpt` files.

## 1. Open the folder containing the downloaded files

Open a Linux terminal and navigate to the folder where you downloaded the chunks.

```bash
cd /path/to/downloaded/files
```

Replace `/path/to/downloaded/files` with your actual folder path.

## 2. Check that all chunks are present

```bash
ls -lh
```

Make sure you have all the chunks for both models before continuing.

For example:

```text
base_00.bin
base_01.bin
large_00.bin
large_01.bin
```

Your actual filenames may be different.

## 3. Reassemble the Base model

Join the Base model chunks in their original order.

```bash
cat base_00.bin base_01.bin > base.ckpt
```

Replace the example chunk names with your actual filenames.

## 4. Reassemble the Large model

Join the Large model chunks in their original order.

```bash
cat large_00.bin large_01.bin > large.ckpt
```

Replace the example chunk names with your actual filenames.

## 5. Verify the output files

Check that both checkpoint files were created successfully.

```bash
ls -lh base.ckpt large.ckpt
```

The resulting files should have approximately the same sizes as the original Base and Large checkpoint files.

## Important Notes

* **Keep the chunks in the correct order.** Joining them incorrectly will corrupt the resulting checkpoint.
* **Do not delete the `.bin` chunks** until you have confirmed that both `.ckpt` files work correctly.
* **Ensure you have enough disk space** for the downloaded chunks and the reconstructed files.
* If your chunk filenames differ from the examples, update the commands accordingly.

Once reassembled, configure your application to load `base.ckpt` and `large.ckpt` from their respective file paths.
