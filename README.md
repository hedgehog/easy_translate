## EasyTranslate - Google Translate (with Bulk translate) in Ruby

I looked around a bit for a google translate library in Ruby that would perform bulk calls and handle user_ips and API keys properly.  There didn't seem to be any, so I made one.

---

### Installation

    $ gem install easy_translate

If you're using Bundler:

    gem 'easy_translate'

And if you're not:

    require 'rubygems'
    require 'easy_translate'

---

### Single translation

    # auto-detect
    EasyTranslate.translate('Hello, world', :to => :spanish) # => "Hola, mundo"
    EasyTranslate.translate('Hello, world', :to => 'es') # => "Hola, mundo"

    # feel free to specify explicitly 
    EasyTranslate.translate('Hola, mundo', :from => :spanish, :to => :en) # => "Hello, world"

---

### Batch translation (Yay!)

    # multiple strings
    EasyTranslate.translate(['Hello', 'Goodbye'], :to => :spanish) # => ["¡Hola", "Despedida"]

    # multiple languages
    EasyTranslate.translate('Hello', :to => [:spanish, :french]) # => ["¡Hola", "Bonjour"]

    # or both?
    EasyTranslate.translate(['Hello', 'Goodbye'], :to => [:es, :it]) # => [['¡Hola', 'Despedida'], ['Ciao', 'Addio']]

---

### Compliance

    # make google happy - (NOTE: use these anywhere)
    EasyTranslate.translate('Hello, world', :to => :es, :key => 'xxx', :user_ip => '127.0.0.1')

    # don't want to set the key on every call? ** Me either! **
    EasyTranslate.api_key = 'xxx'

---

### Because you might be greedy and want detection, too

    # detect language
    EasyTranslate.detect "This is definitely English!" # => 'en'

### What if everything is buried in html?

    # mention that you're submitting HTML (translate calls only)
    EasyTranslate.translate("<b>Hello</b>", :html => true) # => "<b>¡Hola</b>"

---

### List of languages

    # list from <http://translate.google.com/>
    EasyTranslate::LANGUAGES # => { 'en' => 'english', ... }

---

### EasyTranslate in PHP

[Kofel](https://github.com/Kofel) ported this library to PHP. 
You can find the port at https://github.com/Kofel/EasyTranslate

---

### Author

* John Crepezzi - john.crepezzi@gmail.com

---

### License

(The MIT License)

Copyright © 2010-2011 John Crepezzi

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the ‘Software’), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED ‘AS IS’, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
