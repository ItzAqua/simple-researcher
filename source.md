# Source Code
```c#
// Credit to ItzAqua
// https://github.com/ItzAqua/simple-researcher/

public static void Researcher(string file, string hex, int position) {
  using(BinaryReader bReader = new BinaryReader(File.Open(file, FileMode.Open))) {
    bReader.BaseStream.Position = position;

    while(true) {
      string currentHex = BitConverter.ToString(bReader.ReadBytes(hex.Replace(" ", string.Empty).Length / 2)).Replace("-", " ");

      if(currentHex == hex) {
        Console.WriteLine($"[LOG] {hex} / {bReader.BaseStream.Position-1}");
      }
      
      if(bReader.BaseStream.Position >= bReader.BaseStream.Length) {
        break;
      } else {
        bReader.BaseStream.Position = bReader.BaseStream.Position + hex.Replace(" ", string.Empty).Length;
      }
    }
  }
}
```
