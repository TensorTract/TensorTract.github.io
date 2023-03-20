

[//]: #      <center>
[//]: #        <a href="" class="btn2">• GitHub •</a>
[//]: #       <a href="" class="btn2">• Paper •</a></li>
[//]: #       <a href="" class="btn2">• Examples •</a></li>
[//]: #      </center>

<div style="text-align: center;">
<h2><b>Self-Supervised Solution to the Control Problem of Articulatory Synthesis</b></h2>
<p> Interspeech 2023, Authors will be revealed upon paper acceptance </p>
<p> Code, models and the paper itself will be published upon paper acceptance </p>
</div>

<br>
<div style="text-align: center;">
<h3>Abstract</h3>
</div>
<div style="text-align: justify"> 
Given an articulatory-to-acoustic forward model, it is a priori unknown how its motor control must be operated to achieve a desired acoustic result. This control problem is a fundamental issue of articulatory speech synthesis and the cradle of acoustic-to-articulatory inversion, a discipline which attempts to address the issue by the means of various methods. This work presents an end-to-end solution to the articulatory control problem, in which synthetic motor trajectories of Monte-Carlo-generated artificial speech are linked to input modalities (such as natural speech recordings or phoneme sequence input) via speaker-independent latent representations of a vector-quantized variational autoencoder. The proposed method is self-supervised and thus, in principle, synthesizer and speaker model independent.
</div>

<br>
<div style="text-align: center;">
<a id="functionality">
</a>
<div style="text-align: center;">
<h2>TensorTract Functionality</h2>
</div>

<div style="text-align: justify"> 
TensorTract is a compound model of multiple deep neural networks. It is capable to perform a number of tasks including acoustic-to-articulatory inversion (AAI), phoneme-to-articulatory conversion (P2A) and articulatory-to-acoustic neural speech synthesis. In case of AAI and P2A, TensorTract provides articulatory trajectories that are compatible with the state-of-the-art articulatory speech synthesizer VocalTractLab (VTL).
</div>
<br>
<br>
<img
  src="images/TensorTract_schematic.svg"
  alt="Schematic of the TensorTract model."
  height="300"
  />
<br>
<br>
<div style="text-align: justify;">
The centerpiece of TensorTract is a vector-quantized variational autoencoder (VQ-VAE), which maps log-melspectrograms via an TCN-based encoder to a speaker independent quantized latent representation and then back to log-mel features via a speaker and pitch conditioned TCN decoder. The VQ-VAE is trained on both natural and synthetic speech, whereby the latter is generated randomly using VTL. In subsequent training processes, the synthetic articulatory trajectories are mapped to the quantized latent via a multihead attention (MHA)-BiGRU forward model M2L (motor-to-latent) and a respective inverse model L2M (latent-to-motor). This creates a link between natural speech data and synthetic articulatory trajectories. Further, phoneme annotations of the natural speech are mapped to the latent via MHA+TCN-based forward model P2L (phoneme-to-latent). This effectively enables the control of VTL via natural speech and/or phoneme sequence input.
</div>

<div style="text-align: left">
The following abbreviations have been used in the tables below:
</div>
<div style="text-align: left">
<ul>
<li>
<b>P2L+V:</b> Phoneme sequence was mapped to the latent using the P2L model, then the latent was decoded using the L2M model. The rsulting articulatory trajectories were synthesized with VTL.
</li>
<li>
<b>VTL (Rule-based):</b> Speech was synthesized using the rule-based phoneme-to-speech functionality of VTL, which is based on vocal tract state presets derived from magnetic resonance imaging data.
</li>
<li>
<b>M2L+H:</b> The motor trajectories obtained from the VTL (Rule-based) configuration were synthesized using the M2L model and a pretrained Hifi-GAN. The speaker identity of the original natural speakers were used in the decoder.
</li>
<li>
<b>M2L+H (V-ID):</b> Similar to M2L+H, but the speaker identity of the VTL speaker was used in the decoder.
</li>
<li>
<b>L2M+V:</b> Audio input features were mapped to the latent using the VQ-VAE encoder, then the latent was decoded using the L2M model. The rsulting articulatory trajectories were synthesized with VTL.
</li>
<li>
<b>L2M+H:</b> Audio input features were mapped to the latent using the VQ-VAE encoder, then the latent was decoded using the L2M model. The resulting articulatory trajectories were synthesized using the M2L model and a pretrained Hifi-GAN. The speaker identity of the original natural speakers were used in the decoder.
</li>
<li>
<b>L2M+H (V-ID):</b> Similar to L2M+H, but the speaker identity of the VTL speaker was used in the decoder.
</li>
<li>
<b>VQV+H (V-ID):</b> Audio input features were encoded and decoded using the VQ-VAE model. The decoded features were synthesized using Hifi-GAN.
</li>
</ul>
</div>
<div style="text-align: justify">
Note that Hifi-GAN was not fine-tuned to the reconstructed features. Thus, the syntheses with Hifi-GAN do not sound as natural as they could.
</div>

<br>
<div style="text-align: center;">
<a id="audio_examples">
</a>
<div style="text-align: center;">
<h2>Phoneme-to-Articulatory Conversion</h2>
</div>

<p><b>Tested on natural phoneme sequences</b> (KIEL data set, Berlin sentences).</p>


<p><b>Please note:</b> The audio files can be played with Firefox and Google Chrome, but problems were noticed when playing on Safari.</p>

<table border="1">
<tr><td>Model</td><td colspan="12"> Utterances </td></tr>
<tr>
  <td></td>
 
  <td>k02be001</td>
  <td>k02be002</td>
  <td>k02be003</td>
  <td>k02be004</td>
  <td>k02be005</td>
  <td>k02be006</td>
  <td>k02be007</td>
  <td>k02be008</td>
  <td>k02be009</td>
  <td>k02be010</td>

  <td>k61be001</td>
  <td>k61be002</td>
  <td>k61be003</td>
  <td>k61be004</td>
  <td>k61be005</td>
  <td>k61be006</td>
  <td>k61be007</td>
  <td>k61be008</td>
  <td>k61be009</td>
  <td>k61be010</td>
</tr>

<tr><td>Reference</td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k02be001.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k02be002.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k02be003.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k02be004.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k02be005.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k02be006.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k02be007.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k02be008.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k02be009.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k02be010.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k61be001.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k61be002.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k61be003.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k61be004.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k61be005.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k61be006.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k61be007.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k61be008.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k61be009.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k61be010.wav"></audio></td>
</tr>
<tr><td>P2L+V</td>
  <td><audio controls style="width: 110px;" src="audio_examples/p2l/KIELk02_k02be001.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/p2l/KIELk02_k02be002.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/p2l/KIELk02_k02be003.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/p2l/KIELk02_k02be004.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/p2l/KIELk02_k02be005.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/p2l/KIELk02_k02be006.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/p2l/KIELk02_k02be007.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/p2l/KIELk02_k02be008.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/p2l/KIELk02_k02be009.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/p2l/KIELk02_k02be010.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/p2l/KIELk61_k61be001.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/p2l/KIELk61_k61be002.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/p2l/KIELk61_k61be003.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/p2l/KIELk61_k61be004.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/p2l/KIELk61_k61be005.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/p2l/KIELk61_k61be006.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/p2l/KIELk61_k61be007.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/p2l/KIELk61_k61be008.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/p2l/KIELk61_k61be009.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/p2l/KIELk61_k61be010.wav"></audio></td>
</tr>
<tr><td>VTL (Rule-based)</td>
  <td><audio controls style="width: 110px;" src="audio_examples/vtl/k02_k02be001.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vtl/k02_k02be002.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vtl/k02_k02be003.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vtl/k02_k02be004.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vtl/k02_k02be005.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vtl/k02_k02be006.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vtl/k02_k02be007.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vtl/k02_k02be008.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vtl/k02_k02be009.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vtl/k02_k02be010.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vtl/k61_k61be001.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vtl/k61_k61be002.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vtl/k61_k61be003.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vtl/k61_k61be004.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vtl/k61_k61be005.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vtl/k61_k61be006.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vtl/k61_k61be007.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vtl/k61_k61be008.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vtl/k61_k61be009.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vtl/k61_k61be010.wav"></audio></td>
</tr>
<tr><td>M2L+H</td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l/k02_k02be001_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l/k02_k02be002_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l/k02_k02be003_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l/k02_k02be004_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l/k02_k02be005_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l/k02_k02be006_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l/k02_k02be007_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l/k02_k02be008_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l/k02_k02be009_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l/k02_k02be010_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l/k61_k61be001_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l/k61_k61be002_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l/k61_k61be003_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l/k61_k61be004_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l/k61_k61be005_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l/k61_k61be006_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l/k61_k61be007_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l/k61_k61be008_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l/k61_k61be009_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l/k61_k61be010_generated_e2e.wav"></audio></td>
</tr>
<tr><td>M2L+H (V-ID)</td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l_mc_id/k02_k02be001_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l_mc_id/k02_k02be002_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l_mc_id/k02_k02be003_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l_mc_id/k02_k02be004_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l_mc_id/k02_k02be005_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l_mc_id/k02_k02be006_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l_mc_id/k02_k02be007_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l_mc_id/k02_k02be008_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l_mc_id/k02_k02be009_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l_mc_id/k02_k02be010_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l_mc_id/k61_k61be001_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l_mc_id/k61_k61be002_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l_mc_id/k61_k61be003_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l_mc_id/k61_k61be004_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l_mc_id/k61_k61be005_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l_mc_id/k61_k61be006_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l_mc_id/k61_k61be007_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l_mc_id/k61_k61be008_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l_mc_id/k61_k61be009_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/m2l_mc_id/k61_k61be010_generated_e2e.wav"></audio></td>
</tr>


</table>

<br>
<p><b>Zero-shot phoneme-to-speech</b> (unseen speakers, unseen utterances from KIEL data set, Siemens sentences).</p>

<table border="1">
<tr><td>Model</td><td colspan="12"> Utterances </td></tr>
<tr>
  <td></td>
 
  <td>dlmsi038</td>
  <td>dlmsi063</td>
  <td>dlmsi064</td>
  <td>dlmsi072</td>
  <td>dlmsi092</td>

</tr>

<tr><td>Reference</td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/dlmsi038.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/dlmsi063.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/dlmsi064.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/dlmsi072.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/dlmsi092.wav"></audio></td> 
</tr>
<tr><td>P2L+V</td>
  <td><audio controls style="width: 110px;" src="audio_examples/p2l_zero/KIELdlm_dlmsi038.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/p2l_zero/KIELdlm_dlmsi063.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/p2l_zero/KIELdlm_dlmsi064.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/p2l_zero/KIELdlm_dlmsi072.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/p2l_zero/KIELdlm_dlmsi092.wav"></audio></td>
</tr>
<tr><td>VTL (Rule-based)</td>
  <td><audio controls style="width: 110px;" src="audio_examples/vtl/dlm_dlmsi038.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vtl/dlm_dlmsi063.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vtl/dlm_dlmsi064.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vtl/dlm_dlmsi072.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vtl/dlm_dlmsi092.wav"></audio></td>
</tr>


</table>

<br>
<div style="text-align: center;">
<a id="acoustic_to_articulatory_inversion">
</a>
<h2>Acoustic-to-Articulatory Inversion</h2>
</div>

<p><b>Tested on natural audio samples</b> (KIEL data set, Berlin sentences).</p>

<table border="1">
<tr><td>Model</td><td colspan="12">Utterances </td></tr>
<tr>
  <td></td>
 
  <td>k61be011</td>
  <td>k61be018</td>
  <td>k61be023</td>
  <td>k61be030</td>
  <td>k61be037</td>
  <td>k61be061</td>
  <td>k62be005</td>
  <td>k62be024</td>
  <td>k62be086</td>
  <td>k62be095</td>

  <td>k65be002</td>
  <td>k65be013</td>
  <td>k65be017</td>
  <td>k65be075</td>
  <td>k65be077</td>
  <td>k66be008</td>
  <td>k66be041</td>
  <td>k66be060</td>
  <td>k66be062</td>
  <td>k66be063</td>
</tr>


<tr><td>Reference</td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k61be011.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k61be018.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k61be023.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k61be030.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k61be037.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k61be061.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k62be005.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k62be024.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k62be086.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k62be095.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k65be002.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k65be013.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k65be017.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k65be075.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k65be077.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k66be008.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k66be041.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k66be060.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k66be062.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/k66be063.wav"></audio></td>
</tr>
<tr><td>L2M+V</td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/k61be011.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/k61be018.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/k61be023.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/k61be030.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/k61be037.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/k61be061.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/k62be005.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/k62be024.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/k62be086.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/k62be095.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/k65be002.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/k65be013.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/k65be017.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/k65be075.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/k65be077.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/k66be008.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/k66be041.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/k66be060.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/k66be062.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/k66be063.wav"></audio></td>
</tr>
<tr><td>L2M+H</td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l/KIELk61_k61be011_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l/KIELk61_k61be018_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l/KIELk61_k61be023_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l/KIELk61_k61be030_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l/KIELk61_k61be037_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l/KIELk61_k61be061_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l/KIELk62_k62be005_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l/KIELk62_k62be024_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l/KIELk62_k62be086_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l/KIELk62_k62be095_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l/KIELk65_k65be002_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l/KIELk65_k65be013_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l/KIELk65_k65be017_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l/KIELk65_k65be075_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l/KIELk65_k65be077_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l/KIELk66_k66be008_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l/KIELk66_k66be041_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l/KIELk66_k66be060_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l/KIELk66_k66be062_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l/KIELk66_k66be063_generated_e2e.wav"></audio></td>
</tr>
<tr><td>L2M+H (V-ID)</td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l_mc_id/KIELk61_k61be011_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l_mc_id/KIELk61_k61be018_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l_mc_id/KIELk61_k61be023_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l_mc_id/KIELk61_k61be030_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l_mc_id/KIELk61_k61be037_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l_mc_id/KIELk61_k61be061_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l_mc_id/KIELk62_k62be005_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l_mc_id/KIELk62_k62be024_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l_mc_id/KIELk62_k62be086_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l_mc_id/KIELk62_k62be095_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l_mc_id/KIELk65_k65be002_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l_mc_id/KIELk65_k65be013_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l_mc_id/KIELk65_k65be017_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l_mc_id/KIELk65_k65be075_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l_mc_id/KIELk65_k65be077_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l_mc_id/KIELk66_k66be008_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l_mc_id/KIELk66_k66be041_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l_mc_id/KIELk66_k66be060_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l_mc_id/KIELk66_k66be062_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m_m2l_mc_id/KIELk66_k66be063_generated_e2e.wav"></audio></td>
</tr>
<tr><td>VQV+H</td>
  <td><audio controls style="width: 110px;" src="audio_examples/vqvae/KIELk61_k61be011_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vqvae/KIELk61_k61be018_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vqvae/KIELk61_k61be023_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vqvae/KIELk61_k61be030_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vqvae/KIELk61_k61be037_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vqvae/KIELk61_k61be061_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vqvae/KIELk62_k62be005_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vqvae/KIELk62_k62be024_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vqvae/KIELk62_k62be086_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vqvae/KIELk62_k62be095_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vqvae/KIELk65_k65be002_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vqvae/KIELk65_k65be013_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vqvae/KIELk65_k65be017_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vqvae/KIELk65_k65be075_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vqvae/KIELk65_k65be077_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vqvae/KIELk66_k66be008_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vqvae/KIELk66_k66be041_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vqvae/KIELk66_k66be060_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vqvae/KIELk66_k66be062_generated_e2e.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/vqvae/KIELk66_k66be063_generated_e2e.wav"></audio></td>
</tr>

</table>



<br>
<p><b>Tested on natural utterances</b> (MLS German data set).</p>
<div style="text-align: justify;">
Here we demonstrate how the intelligibility of the produced samples increases if the acoustic noise (which is induced by articulatory noise) is suppressed. Future work should address how to regularize the neural network to output smooth, non-noisy articulatory trajectories in case of natural speech input where no motor loss is available. In the table <b>NR</b> means noise reduction is applied.
</div>

<table border="1">
<tr><td>Model</td><td colspan="12"> Utterances </td></tr>
<tr>
  <td></td>
 
  <td>252_1614_000008</td>
  <td>2497_1614_000000</td>
  <td>10148_10119_000697</td>

</tr>

<tr><td>Reference</td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/252_1614_000008.flac"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/2497_1614_000000.flac"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/10148_10119_000697.flac"></audio></td>
</tr>
<tr><td>L2M+V (NR)</td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/252_1614_000008_enhanced.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/2497_1614_000000_enhanced.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/10148_10119_000697_enhanced.wav"></audio></td>
</tr>
<tr><td>L2M+V</td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/252_1614_000008.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/2497_1614_000000.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/10148_10119_000697.wav"></audio></td>
</tr>


</table>


<br>
<p><b>Tested on unseen languages</b> (LJSpeech, LibriSpeech, aishell-3).</p>
<div style="text-align: justify;">
Here we demonstrate the acoustic-to-articulatory inversion on other languages. This is challenging, as the audio encoder has never seen the speakers, utterances, or languages during training.
</div>
<br>

<b>English:</b>


<table border="1">
<tr><td>Model</td><td colspan="12"> Utterances </td></tr>
<tr>
  <td></td>
 
  <td>LJ001_0001</td>
  <td>1320_122612_0000</td>
  <td>LJ001_0024</td>
  <td>1320_122612_0012</td>

</tr>

<tr><td>Reference</td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/LJ001_0001.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/1320_122612_0000.flac"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/LJ001_0024.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/1320_122612_0012.flac"></audio></td>
</tr>
<tr><td>L2M+V (NR)</td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/LJ001_0001_1_enhanced.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/1320_122612_0000_enhanced.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/LJ001_0024_enhanced.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/1320_122612_0012_enhanced.wav"></audio></td>
</tr>
<tr><td>L2M+V</td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/LJ001_0001.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/1320_122612_0000.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/LJ001_0024.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/1320_122612_0012.wav"></audio></td>
</tr>


</table>
<br>

<b>Mandarin:</b>

<table border="1">
<tr><td>Model</td><td colspan="12"> Utterances </td></tr>
<tr>
  <td></td>
 
  <td>A</td>
  <td>B</td>
  <td>C</td>

</tr>

<tr><td>Reference</td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/aishell3_example_8.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/aishell3_example_10.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/nat/aishell3_example_11.wav"></audio></td>
</tr>
<tr><td>L2M+V (NR)</td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/aishell3_example_8_enhanced.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/aishell3_example_10_enhanced.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/aishell3_example_11_enhanced.wav"></audio></td>
</tr>
<tr><td>L2M+V</td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/aishell3_example_8.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/aishell3_example_10.wav"></audio></td>
  <td><audio controls style="width: 110px;" src="audio_examples/l2m/aishell3_example_11.wav"></audio></td>
</tr>


</table>
