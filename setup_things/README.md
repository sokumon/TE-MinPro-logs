
# Blockly Setup (that works) 😎

Download node not from a tree but from the web :)




## How to do it?

run the following command

```bash
  npm install blockly@5.2
```
Create a index.html in the same directory as the node modules
Add the following script tages into that index.html
```JavaScript 
    <script src="node_modules/blockly/blockly_compressed.js"></script>
    <script src="node_modules/blockly/blocks_compressed.js"></script>
    <script src="node_modules/blockly/python_compressed.js"></script>
    <script src="node_modules/blockly/msg/en.js"></script>
    <script src ="index.js"></script>
```
Write this in index.js to see if it works
```JavaScript 
const emojiLang = new Blockly.Generator('EmojiLang');

emojiLang['print'] = function (block) {
  const code = block.getFieldValue('EMOJI_CODE');
  if (!code) return 'waiting…';
  if (code == ':-)') return '🙂';
  if (code == ':-(') return '🙁';
  if (code == ':-/') return '😕';
  return '(unknown)';
};

Blockly.defineBlocksWithJsonArray([
  {
    type: 'print',
    message0: 'print %1',
    args0: [
      { type: 'field_input', name: 'EMOJI_CODE' }
    ]
  }
]);

const ws = Blockly.inject('blocklyDiv', {
  toolbox: {
    kind: 'flyoutToolbox',
    contents: [
      { kind: 'block', type: 'print' }
    ]
  }
});

ws.addChangeListener(function () {
  document.getElementById('textarea').innerHTML =
    emojiLang.workspaceToCode(ws);
});

```

![Blockly Setup](https://github.com/sokumon/TE-MiniPro-Logs/blob/main/blockly.png?raw=true)

