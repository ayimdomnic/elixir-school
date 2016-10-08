---
layout: page
title: Behaviours
category: advanced
order: 
lang: en
---

We learned about Typespecs the previous lesson, here we'll learn about how to require a module implement those specifications.  In Elixir, this functionality is referred to as Behaviours.

{% include toc.html %}

## Uses

Behaviours give us the ability to define a set of functions a module must implement and ensure that set has been implemented, this makes it easy to create and share a public API.

There are a number of behaviours built into Elixir, like GenServer but there's nothing stopping us from creating out own.


## Defining a behaviour

To get a closer look let's implement a behaviour for a worker module.  These workers will be expected to implement three functions: `init/1`, `perform/2`, and finally `cleanup/1`.  To accomplish this we'll use the `@callback` directive to specify our required methods using a similar syntax to `@spec`:

```elixir
defmodule Example.Worker do
  @callback init(state :: term) :: {:ok, new_state :: term} | {:error, reason :: term}
  @callback perform(args :: term, state :: term) :: {:ok, result :: term, new_state :: term} | {:error, reason :: term, new_state :: term}
  @callback cleanup(state :: term) :: :ok
end
```

This 

## Using behaviours

```elixir
defmodule Example.CSV do
  use Example.Worker
  
  def init(opts), do {:ok, opts}
  
  def perform(, opts) do
  end
  
  def cleanup(opts) do
    :ok
  end
end
```