All notable changes to this project will be documented in this file.

This project adheres to [Semantic Versioning](http://semver.org/spec/v2.0.0.html).


## Unreleased

### Breaking changes

### Compatible changes

- support rails 7

## 1.1.0 - 2021-09-28

### Breaking changes

- remove no longer supported ruby versions (2.3.8, 2.4.5)
- Consul no longer depends on the whole rails framework

### Compatible changes

- add Ruby 3 compatibility

## 1.0.3 - 2019-09-23

### Security fix

This releases fix a security issue where in a controller with multiple `power` directives, the `:only` and `:except` options of the last directive was applied to all directives.

Affected code looks like this:

```ruby
class UsersController < ApplicationController
  power :foo
  power :bar, only: :index

  ...
end
```

In this example both the powers `:foo` and `:bar` were only checked for the `#index` action. Other actions were left unprotected by powers checks.

Controllers with a single `power` directive are unaffected.
Contollers where neither `power` uses `:only` or `:except` options are unaffected.

This vulnerability has been assigned the CVE identifier CVE-2019-16377.


### Compatible changes

- The RSpec matcher `check_power` now also sees powers inherited by a parent controller.


## 1.0.2 - 2019-05-22

### Compatible changes

- The `#arity` of power methods with optional arguments is now preserved.



## 1.0.1 - 2019-02-27

### Compatible changes

- Methods defined with `power` now preserve the [arity](https://apidock.com/ruby/Method/arity) of their block.



## 1.0.0 - 2019-02-15

### Breaking changes

- Removed `Power.for_record(record)`. Use `Power.for_model(record.class)` instead.
- Removed `Power#for_record(record)`. Use `Power#for_model(record.class)` instead.
- Removed `Power#name_for_record(record)`. Use `Power#name_for_model(record.class)` instead.



## 0.14.1 - 2018-11-13

### Compatible changes

- inherit power guards upon controller inheritance (fixes #40)

## 0.14.0 - 2018-10-09

### Breaking changes

- drop support for Rails 2.3

### Compatible changes

- migrate tests to Gemika

## 0.13.2 - 2018-10-02

### Compatible changes

- Bang methods should return the scope when successful (e.g. `power.notes!` returns the scope you defined in the power)
- improve the error message for scoped powers

## 0.13.1 - 2017-09-28

### Compatible changes

- Fix controller integration when using `ActionController::API`.

Thanks to derekprior.


## 0.13.0 - 2017-09-05

### Breaking change

- All powers memoize.


## Older releases

Please check commits.
