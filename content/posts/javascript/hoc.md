---
title: "Higher Order Component"
date: 2021-11-07T15:31:03+13:00

menu:
  sidebar:
    name: Higher Order Component
    identifier: hoc
    parent: java-script
    weight: 10

---

### why we need Higher Order Compnents

There are certian situation where we need to use same logic in differnt places.In that kind of sceanarios HOC play a huge role.Basically HOC  provides follwing  benifts
      
       1. Reusability /Less code duplicatiom
       2. Easy to add functionality

Now let's see the definition of HOC which mentioned in the ReactJS.Org
            
    

    A higher-order component (HOC) is an advanced technique in React for 
    reusing component logic. HOCs are not part of   the React API, per se. They are a pattern that emerges from React’s compositional nature.

lets see how we can implement HOC compnent.In this case I am going to use React HOOK FORM . 
```JavaScript

import { useEffect, useState } from "react";
import { useFieldArray, useForm } from "react-hook-form";

const hoc = (Component) => () => {
  const [results, setResults] = useState([]);

  const { register, control, handleSubmit, reset, watch } = useForm({
    defaultValues: {
      test: [{ firstName: "Bill", lastName: "Luo" }],
    },
  });
  const { fields, append, prepend, remove } = useFieldArray({
    control,
    name: "test",
  });

  return (
    <form>
      <ul>
        {fields.map((item, index) => {
          return (
            <Component
              item={item}
              removeindex={remove}
              index={index}
              {...register(`test.${index}.firstName`)}
            />
          );
        })}
      </ul>
      <section>
        <button
          type="button"
          onClick={() => {
            append({ firstName: "appendBill" });
          }}
        >
          Append
        </button>
      </section>
    </form>
  );
};

export default hoc;

```
As you can see above componnet take another compnent as a paramter.so we can modify the component receving according 
to the logic implemented in the Higher order Component.


Next we will look into how we can pass child component into  Higher order component

```JavaScript

import { useEffect, useState } from "react";
import { useForm, useFieldArray } from "react-hook-form";
import   hoc  from "./hoc"
import { TextField } from "@mui/material";



 
const InputList = props => {
  return (
    <li key={props.item.id}>
      <TextField {...props}></TextField>
      <button onClick={() => props.removeindex(props.index)} type="button">
        Delete
      </button>
    </li>
  );
};
export default hoc(InputList);

```