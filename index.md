<html lang="pt-br">
  <head>
    <meta charset="UTF-8">
    <title>TensorTract</title>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" type="text/css" href="stylesheets/normalize.css" media="screen">
    <link href='https://fonts.googleapis.com/css?family=Open+Sans:400,700' rel='stylesheet' type='text/css'>
    <link rel="shortcut icon" type="image/x-icon" href="favicons/favicon.ico">
    <link rel="stylesheet" type="text/css" href="stylesheets/stylesheet.css" media="screen">
    <link rel="stylesheet" type="text/css" href="stylesheets/github-light.css" media="screen">
  </head>
  <body>
    <section id="page-header" class="page-header">
        <div id="bg-header"></div>
        <canvas id="demo-canvas"></canvas>
        <div class="main-title">
          <h1 class="project-name"><span><a href="index.html">TensorTract</a></span></h1>

          <h2 class="project-tagline">Self-Supervised Solution to the Control Problem of Articulatory Synthesis</h2>

        </div>-->
    </section>

    <section class="main-content">

      <center>
        <a href="" class="btn2">• GitHub •</a>
       <a href="" class="btn2">• Paper •</a></li>
       <a href="" class="btn2">• Examples •</a></li>
      </center>
<div class='particle-network-animation'>
</div>
<div style="text-align: center;">
<h2><b>Self-Supervised Solution to the Control Problem of Articulatory Synthesis</b></h2>
<p> Interspeech 2023, Authors will be revealed upon paper acceptance </p>
</div>

Test

<div style="text-align: center;">
<h3>Abstract</h3>
</div>
<div style="text-align: justify"> 
Given an articulatory-to-acoustic forward model, it is a priori unknown how its motor control must be operated to achieve a desired acoustic result. This control problem is a fundamental issue of articulatory speech synthesis and the cradle of acoustic-to-articulatory inversion, a discipline which attempts to address the issue by the means of various methods. This work presents an end-to-end solution to the articulatory control problem, in which synthetic motor trajectories of Monte-Carlo-generated artificial speech are linked to input modalities (such as natural speech recordings or phoneme sequence input) via speaker-independent latent representations of a vector-quantized variational autoencoder. The proposed method is self-supervised and thus, in principle, synthesizer and speaker model independent.
</div>


<div style="text-align: center;">
<h2>Acoustic-to-Articulatory Inversion</h2>
</div>

<p><b>Tested on natural audio samples</b></p>

<table border="1">
<tr><td>Model</td><td colspan="12">Unseen Speakers </td></tr>
<tr>
  <td></td>
 
	<td>A</td><td>B</td><td>C</td><td>D</td>
	<td>E</td><td>F</td><td>G</td><td>1</td>
	<td>2</td><td>3</td>
</tr>


<tr><td>Reference</td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k61be011.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k61be018.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k61be030.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k61be037.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k61be061.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
</tr>
<tr><td>Condition 1</td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/k61be011.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/k61be018.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/k61be030.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/k61be037.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/k61be061.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
</tr>
<tr><td>Condition 2</td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
</tr>


</table>

<div style="text-align: center;">
<h2>Phoneme-to-Articulatory Conversion</h2>
</div>

<p><b>Audio Samples for other speakers</b></p>

<table border="1">
<tr><td>Model</td><td colspan="12">Unseen Speakers </td></tr>
<tr>
  <td></td>
 
  <td>A</td><td>B</td><td>C</td><td>D</td>
  <td>E</td><td>F</td><td>G</td><td>1</td>
  <td>2</td><td>3</td>
</tr>


<tr><td>Reference</td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
</tr>
<tr><td>Condition 1</td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
</tr>
<tr><td>Condition 2</td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/.wav"></audio></td>
</tr>


</table>


