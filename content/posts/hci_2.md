+++ 
date = "2023-01-29"
title = "HCI Lab2 - Roll Ball Game"
description = "This is about how I created the roll ball game and the questions that arose during my creation process"
authors = "Xuefeng Wei"
slug = "HCI Lab2"
+++
In this one lab, I mainly developed a simple unity game, by controlling the ball collision objects to achieve the role of the destruction of objects, this part is divided into two parts, the first part for how I created this game, the second part is I encountered some problems

## 1. Create the Game
First I created a sphere to be the player, then a plane to be the ground, and four cubes to be the walls, and then created different materials for them to be their colors,Also, on the playfield I created 12 small cubes as game objects, and in groups of 6, each group is a different color, the final scene is shown below:

![hci2-1.png](https://s2.loli.net/2023/01/30/BlnSfXjC7FY912m.png)

The next step is to control the player object by scripts and make the small square rotate

```html
public class PlayerController : MonoBehaviour
{
    public float speed = 0;
    private Rigidbody rb;
    private float movementX;
    private float movementY;
    // Start is called before the first frame update
    void Start()
    {
        rb = GetComponent<Rigidbody>();
    }

    private void OnMove(InputValue movementValue)
    {
        Vector2 movementVector = movementValue.Get<Vector2>();
        movementX = movementVector.x;
        movementY = movementVector.y;
    }

    private void FixedUpdate()
    {
        Vector3 movement = new Vector3(movementX, 0.0f,movementY);
        rb.AddForce(movement * speed);
    }

    private void OnTriggerEnter(Collider other)
    {
        if ((other.gameObject.CompareTag("Pickuporange")) || (other.gameObject.CompareTag("Pickupgreen")))
        {
            other.gameObject.SetActive(false);
        }
    }
```
Above is the script for controlling objects and colliding with them to make them disappear
Here is a video demonstrating this simple game：
https://www.youtube.com/watch?v=lYDTS4OFwVY&feature=youtu.be

##2. Problem I met durng this lab 
In this lab, I encountered fewer problems, mainly focused on scripting, especially in the part of controlling objects, because the first contact with C# language led to more errors.
