# Week 11
### Video Link: https://vimeo.com/1250192463?share=copy&fl=sv&fe=ci
### Player Movement Script
using UnityEngine;
using UnityEngine.InputSystem;

public class PlayerMovement : MonoBehaviour
{
    public float moveSpeed;

    private float speedX = 0f;
    private float speedY = 0f;

    public Rigidbody2D rb;

    void Start()
    {

    }

    void Update()
    {
        Movement();
    }

    void FixedUpdate()
    {
        rb.linearVelocity = new Vector2(speedX, speedY);
    }

    void Movement()
    {
        // Horizontal Movement
        if (Keyboard.current.aKey.isPressed)
        {
            speedX = -moveSpeed;
        }
        else if (Keyboard.current.dKey.isPressed)
        {
            speedX = moveSpeed;
        }
        else
        {
            speedX = 0;
        }

        // Vertical Movement
        if (Keyboard.current.wKey.isPressed)
        {
            speedY = moveSpeed;
        }
        else if (Keyboard.current.sKey.isPressed)
        {
            speedY = -moveSpeed;
        }
        else
        {
            speedY = 0;
        }
    }
}
### Player Health Script
using TMPro;
using UnityEngine;

public class PlayerHealth : MonoBehaviour
{
    public int health = 100;
    public TMP_Text healthText;

    public PlayerHealth(TMP_Text healthText)
    {
        this.healthText = healthText;
    }

    void Start()
    {
        healthText.text = "Health: " + health;
    }
    void Update()
    {
        healthText.text = "Health: " + health;
    }
}
### Trap Script
    using UnityEngine;

public class Trap : MonoBehaviour
{
    public PlayerHealth playerHealth;
    // Start is called once before the first execution of Update after the MonoBehaviour is created
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        
    }

    private void OnTriggerEnter2D(Collider2D collision)
    {
        if (collision.CompareTag("Player"))
        {
            playerHealth.health -= 10;
        }
    }
}
### Healthpack Script
using UnityEngine;

public class HealthPack : MonoBehaviour
{
    public PlayerHealth playerHealth;
    public GameObject healthPack;

    private void OnTriggerEnter2D(Collider2D collision)
    {
        if (collision.CompareTag("Player")) 
        {
            if  (playerHealth.health <= 90)
                playerHealth.health += 10;
        }
        {
            healthPack.SetActive(false);
        }
    }
}