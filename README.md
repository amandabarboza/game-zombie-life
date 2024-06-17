<h1 style="text-align: center;"><b> Zombie Life 🧟🏃 - Game </b></h1>

<h3><b>Descrição do jogo</b></h3>



<h3><b>🎮 Modo de Jogar 🎮</b></h3> 
Teclas A, W, S e D para mover o personagem.

<br>

<h3> Telas do jogo </h3>

<h4>Menu inicial</h4>

<br>

<h3> Funcionalidades </h3>

1. Nevar
   
![nevar](https://github.com/amandabarboza/game-zombie-life/assets/71797931/2085fa83-6ca5-4474-991c-5a6733295834)

2. Pular

![gif_pulo](https://github.com/amandabarboza/game-zombie-life/assets/71797931/cab3b146-ec91-4502-8fcd-e69a4c2afe8f)

<pre>
C#
   
using UnityEngine;

public class SimpleJump : MonoBehaviour
{
    public float jumpHeight = 2f; // Altura do pulo
    public float jumpDuration = 0.5f; // Duração do pulo

    private Vector3 startPosition;
    private Vector3 peakPosition;
    private bool isJumping = false;
    private float timer;

    void Update()
    {
        if (Input.GetKeyDown(KeyCode.Space) && !isJumping)
        {
            isJumping = true;
            timer = 0;
            startPosition = transform.position; // Guarda a posição de início do pulo
            peakPosition = startPosition + Vector3.up * jumpHeight; // Calcula a posição mais alta do pulo
        }

        if (isJumping)
        {
            timer += Time.deltaTime;
            float fraction = timer / jumpDuration;

            if (fraction < 0.5f) // Subindo
            {
                transform.position = Vector3.Lerp(startPosition, peakPosition, fraction * 2);
            }
            else if (fraction < 1f) // Descendo
            {
                transform.position = Vector3.Lerp(peakPosition, peakPosition - Vector3.up * jumpHeight, (fraction - 0.5f) * 2);
            }
            else // Terminou o pulo
            {
                transform.position = peakPosition - Vector3.up * jumpHeight; // Nova posição após o pulo
                isJumping = false;
            }
        }
    }
}
   
</pre>


<h4>Tela principal do jogo</h4>

