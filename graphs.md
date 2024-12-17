## Understanding the Graphs 🚨

> :warning: Yo, this section is a *W.I.P.* — don’t judge me too hard, I still gotta tweak some stuff! 🫣 :warning:

So, I’m gonna break down what these graphs mean in RLGym-PPO, and how you should be reading ‘em. This ain’t no boring lecture, I’ll keep it real with you.

By default, RLGym-PPO logs all the metrics with wandb. If you're vibin’ with wandb, just hit up your bot’s wandb link — it's in the console once you fire up a training sesh.

Heads up: I’m not gonna dive into every little detail on the trickier graphs for now. Maybe in the future I’ll throw in some deep dives if you're really trying to go full-on genius mode.

## Big Tip: Watch Your Bot in Action!

Unless you're tracking your bot's ELO (you know, where different versions of your bot go head-to-head to flex on each other), no graph’s gonna tell you more than just watching your bot in action. Period.

Don’t stress about vague graphs (like the policy reward). Those don’t tell the full story. Freaking out about entropy spikes or clip fraction will just give you a headache. Trust me, graphs like these sometimes do some weird back-and-forth and it’s totally chill. Bots gotta learn, they gon’ make mistakes.

But, if you see a graph that drops or rockets up randomly to some insane value — yeah, something’s off. Don’t use graphs alone to judge progress unless it’s super obvious.

## Policy Reward
![image](https://github.com/ZealanL/RLGym-PPO-Guide/assets/36944229/cb480e81-38c4-488e-9b2a-f563257ef7ca)

Ayy, this graph shows the average reward your bot gets per episode. Early on, you’ll see it rise fast, but don’t trip if it starts to plateau or dip.

The reward is linked to the episode’s length. In the early stages, your bot is probably ending its episodes due to timeouts, so episodes are long. But as soon as your bot starts getting those hits in, goal-scoring becomes the main episode-ender. So, shorter episodes = lower policy reward, simple as that.

From my experience? Early on, this graph will spike up like crazy. Then, once your bot starts smacking the ball around, it’ll flatten out or dip as goal-scoring gets the spotlight.

Oh, and if you're using zero-sum rewards? Yeah, this graph’s basically just white noise. Zero-sum rewards don’t mean much until your bot is actually hitting the ball. Still, it’s decent for tracking early learning vibes.

## Policy Entropy
![image](https://github.com/ZealanL/RLGym-PPO-Guide/assets/36944229/a3974e70-30ae-4cb2-9cf6-3fad02a09fb3)

Now this one’s low-key dope. It shows how much variety your bot has in its actions. If it’s spicing things up, this graph will tell you. The more chaotic or diverse the actions, the higher this value. It’s also linked to 'ent_coef', and like, the situation your bot finds itself in.

## Value Function Loss
![image](https://github.com/ZealanL/RLGym-PPO-Guide/assets/36944229/832d5b31-3bef-4551-ad8e-8dfed9d90d45)

Okay, this graph is your critic’s struggle bus. It shows how hard it is for your bot’s critic to predict the rewards based on its actions. The harder it is to predict — like, when your bot scores goals or pulls off demos — the more this graph is gonna fluctuate.

Early on, expect this to drop a ton. But after a while, it’ll settle to a kind of “best guess” point and chill out, with some slight fluctuations based on your bot’s reward patterns.

Also, if you change your rewards mid-training? This graph is gonna shift real quick.

## Policy Update Magnitude/Value Function Update Magnitude
![image](https://github.com/ZealanL/RLGym-PPO-Guide/assets/36944229/d8726d44-dd0b-42a4-92dc-c0695adb03b7)

These graphs show how much your bot’s policy and critic change with every iteration. If the learning rate is too hot, these will spike like crazy. You’ll see shifts if you mess with the rewards too much too — so keep that in mind.

## SB3 Clip Fraction/Mean KL Divergence
![image](https://github.com/ZealanL/RLGym-PPO-Guide/assets/36944229/ebca338e-bd0b-407a-b5cc-3f4539a54301)

These graphs track how much the policy changes from one iteration to the next. People usually target a specific value here — like ~0.08 for clip fraction, to keep things balanced.

### *To-Do: I’ll add more graphs soon! Stay tuned!* 👀

_____
[Back to Table of Contents](README.md)
