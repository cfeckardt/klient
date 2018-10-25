# klient

* [Homepage](https://rubygems.org/gems/klient)
* [Documentation](http://rubydoc.info/gems/klient/frames)
* [Email](mailto:cfeckardt@gmail.com)

[![Build Status](https://secure.travis-ci.org/cfeckardt/klient.svg?branch=master)](https://travis-ci.org/cfeckardt/klient)
[![Code Climate GPA](https://codeclimate.com/github//klient/badges/gpa.svg)](https://codeclimate.com/github//klient)

## Description

Klient is a Kafka client with opinionated error handling.
*KLIENT IS NOT YET READY FOR USE*
Klient is built on top of ruby-kafka

Klient will offload any errors onto configurable alternative topics, that can be leveraged for exponential back-off while still processing the main topic.

For example, if you have a topic called 'important-job' and some messages fail to process successfully, klient will (by default) move the message to another topic called
important-job.retry1, and attempt to retry with exponential backoff. If the message still fails to retry after n tries, the message will be moved to important-job.dead along with any debugging information.

## Features

* Exponential Backoff

## Examples

    require 'klient'
    
## Basic usage

This project attempts to mimic the API of 'ruby-kafka' wherever possible.

```
klient = Klient.new(uris: ['zk1', 'zk2'])

klient.subscribe('consumer_group')

klient.each_message do |message|
  
end
```


## Install

    $ gem install klient

## Copyright

Copyright (c) 2018 Fredrik Eckardt

See {file:LICENSE.txt} for details.
