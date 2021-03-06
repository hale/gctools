## gctools

gc profiler/logger and oobgc for rgengc in ruby 2.1

oobgc is unnecessary in Ruby 2.2, since it includes an incremental GC (RIncGC) and will not pause the world for a long time.

### design

built on new apis and events offered in ruby 2.1:

  * rb_gc_stat()
  * rb_gc_latest_gc_info()
  * RUBY_INTERNAL_EVENT_GC_START
  * RUBY_INTERNAL_EVENT_GC_END_MARK
  * RUBY_INTERNAL_EVENT_GC_END_SWEEP

### usage

#### logger

``` ruby
require 'gctools/logger'
```

#### oobgc

``` ruby
require 'gctools/oobgc'
GC::OOB.run # after every request
use(GC::OOB::UnicornMiddleware) # in config.ru for unicorn
```
