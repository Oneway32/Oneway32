- 👋 Hi, I’m @Oneway32
- 👀 I’m interested in GIT
- 🌱 I’m currently learning Git hub 
- 💞️ I’m looking to collaborate on ... REPOSITORY 
- 📫 How to reach me ... @oneway32
- ⚡ Fun fact: ... I'm cheating on my Girlfriend with my EX

<!---
Oneway32/Oneway32 is a ✨ special ✨ repository because its `README.md
dbb3da310653a6ed07b41da775cdfe1f313b952c#!/usr/bin/env node

var argv = require('optimist').argv;
var through = require('through');
var split = require('split');

var term = [argv.t || argv.term].concat(argv._).join(' ').trim();

var filterEmpty = function (f) { return !!f.length; };

var extractData = function (val) {
  return val.toString()
            .split('\n')
            .filter(filterEmpty)
};

var jsonParse = function (str) {
  try {
    return JSON.parse(str);
  } catch (e) {
    return {};
  }
};

var processLine = function (line) {

  if (!line.length) return;

  try {
    this.queue(require('util').inspect(jsonParse(line), {
      depth: null, colors: true
    }) + '\n\n');
  } catch (e) {
    this.queue('Error, failed to inspect ' + line);
  }

};

process.stdin
  .pipe(split())
  .pipe(through(processLine))
  .pipe(process.stdout);