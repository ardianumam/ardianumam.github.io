---
layout: project_page
permalink: /partdistill/
title: PartDistill (CVPR 2024)
nav: false
---
<!-- Head -->
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, shrink-to-fit=yes">
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<title>{{page.title}}</title>
</head>

          
<!-- sticky-top or fixed-top-->
 

<!-- <nav class="project-page-nav"  style="text-align: center; width:100%; background-color: #fff; box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);"> -->
<nav class="project-page-nav">
  <ul style="margin: 0.3rem">
    <li style="display: inline-block;">
      <div class="project-page-home-button">
          <a href="{{site.url}}" target="_self" class="hyperlink">
            <i class="fas fa-home home-icon"></i>
          </a>
      </div>
    </li>
    <li style="display: inline-block;">
      <button id="back-to-top" class="project-page-home-button">
        <i class="fas fa-arrow-up"></i>
      </button>
    </li>
    <li style="display: inline-block;">
      <div class="theme-container">
        <button id="theme-button" style="padding: 10px 10px;" title="Change theme">
          <i class="fas fa-lightbulb"></i>
        </button>
          <div class="theme-options">
            <button id="light-button">
              <i class="ti ti-sun-filled" id="light-icon"></i> (light)
              </button>
            <button id="dark-button">
              <i class="ti ti-moon-filled" id="dark-icon"></i> (dark)
            </button>
          </div>
      </div>
    </li>
  </ul>
</nav>

<br>

<body>
  <div class="container research">
    <!-- Title and authors -->
    <h1 style="text-align: center; font-weight: bold; margin-bottom:0.9rem;">PartDistill: 3D Shape Part Segmentation by Vision-Language Model Distillation</h1>
    <div class="author"> 
      <a href="https://ardianumam.github.io/">Ardian Umam<sup>1</sup></a> 
      <a href="https://scholar.google.com/citations?user=Ke4_ozgAAAAJ&hl=en&oi=sra">Cheng-Kun Yang<sup>2</sup></a>
      <a href="https://minhungchen.netlify.app/">Min-Hung Chen<sup>3</sup></a>
      <a href="https://www.cs.nycu.edu.tw/members/detail/jchuang">Jen-Hui Chuang<sup>1</sup></a> 
      <a href="https://sites.google.com/site/yylinweb/">Yen-Yu Lin<sup>2</sup></a>
    </div>
    <div class="author"><sup>1</sup>National Yang Ming Chiao Tung University <sup>2</sup>MediaTek <sup>3</sup>NVIDIA</div>
    <h4 style="text-align: center; font-weight: bold; margin-top: 0.9rem">CVPR 2024</h4>
    <!-- Hyperlink buttons -->
    <!-- <div class="row text-center">
      <div class="col d-flex justify-content-center">
        <a href="https://arxiv.org/abs/2312.04016" class="hyperlink-button">
          <span class="hyperlink-button-text">Paper</span>
          <i class="ai ai-arxiv"></i>
        </a>
        <a href="#" class="hyperlink-button">
          <span class="hyperlink-button-text">Poster</span>
          <i class="fa fa-file-pdf"></i>
        </a>
        <a href="https://github.com/ardianumam/PartDistill" class="hyperlink-button">
          <span class="hyperlink-button-text">Code</span>
          <i class="fab fa-github"></i>
        </a>
        <a href="#" class="hyperlink-button">
          <span class="hyperlink-button-text">Video</span>
          <i class="fas fa-video"></i>
        </a>
      </div>
    </div> -->

    <div class="container text-center">
      <div class="column has-text-centered">
        <a href="https://arxiv.org/abs/2312.04016" class="hyperlink-button">
          <span class="hyperlink-button-text">Paper</span>
          <i class="ai ai-arxiv"></i>
        </a>
      
        <a href="#" class="hyperlink-button">
          <span class="hyperlink-button-text">Poster</span>
          <i class="fa fa-file-pdf"></i>
        </a>
      
        <a href="https://github.com/ardianumam/PartDistill" class="hyperlink-button">
          <span class="hyperlink-button-text">Code</span>
          <i class="fab fa-github"></i>
        </a>
      
        <a href="#" class="hyperlink-button">
          <span class="hyperlink-button-text">Video</span>
          <i class="fas fa-video"></i>
        </a>
      </div>
    </div>
  

    <br><br>

    <!-- Abstract -->
    <h2 style="text-align: center;">Abstract</h2>
    <div class="content">
    We propose a cross-modal distillation framework, PartDistill, which transfers 2D knowledge from vision-language models (VLMs) to facilitate 3D shape part segmentation. PartDistill addresses three major issues in this task, namely \(\boldsymbol{\mathcal{I}_1}\): the lack of 3D segmentation in invisible or undetected regions in the 2D projections, \(\boldsymbol{\mathcal{I}_2}\): inconsistent 2D predictions by VLMs, and \(\boldsymbol{\mathcal{I}_3}\): the lack of knowledge accumulation across different 3D shapes. PartDistill consists of a teacher network that uses a VLM to make 2D predictions and a student network that learns from the 2D predictions while extracting geometrical features from multiple 3D shapes to carry out 3D part segmentation. A bidirectional distillation, including forward and backward distillations, is carried out within the framework, where the former forward distills the 2D predictions to the student network, and the latter improves the quality of the 2D predictions, which subsequently enhances the final 3D segmentation. Moreover, PartDistill can exploit generative models that facilitate effortless 3D shape creation for generating knowledge sources to be distilled. Through extensive experiments, PartDistill boosts the existing methods with substantial margins on widely used ShapeNetPart and PartNetE datasets, by more than 15% and 12% higher mIoU scores, respectively.
    </div>
    <br>

    <!-- Method -->
    <h2 style="text-align: center;">Method</h2>
    <img src="/assets/img/project_page/2024_partdistill/main_fig.png" alt="Architecture of PartDistill" class="img-fluid mx-auto d-block">
    <div class="content" style="margin-top: 1rem">
    <b>Overview of the proposed method.</b> (a) The overall pipeline where the knowledge extracted from a vision-language model (VLM) is distilled to carry out 3D shape part segmentation by teaching a 3D student network. Within the pipeline, <em>backward distillation</em> is introduced to re-score the teacher’s knowledge based on its quality and subsequently improve the final 3D part prediction. (b) & (c) Knowledge is extracted by back-projection when we adopt (b) a bounding-box VLM (B-VLM) or (c) a pixel-wise VLM (P-VLM).
    </div>
    <br>

    <!-- Experimental results -->
    <h2 style="text-align: center;">Experimental Results</h2>
    <h4 style="text-align: center;">Qualitative results</h4>
    <img src="/assets/img/project_page/2024_partdistill/qualitative_result.png" alt="Qualitative results" class="img-fluid mx-auto d-block">
    <div class="content" style="margin-top: 1rem">
    Visualization of the zero-shot segmentation results, drawn in different colors, on the ShapeNetPart dataset. We render PartSLIP results on the ShapeNetPart data to have the same visualization of shape inputs. While issue \(\boldsymbol{\mathcal{I}_1}\): occluded and undetected regions are shown with black and gray colors, respectively, the blue and red arrows highlight several cases of issues \(\boldsymbol{\mathcal{I}_2}\): negative transfer and \(\boldsymbol{\mathcal{I}_3}\): lack of knowledge accumulation.
    </div>

    <br>
    <h4 style="text-align: center;">Quantitative results</h4>
    <img src="/assets/img/project_page/2024_partdistill/quantitative_result1.png" alt="Quantitative results" class="img-fluid mx-auto d-block">
    <div class="content" style="margin-top: 1rem">
    We carry out the comparison separately to ensure fairness, based on the employed VLM model and the shape data type, i.e., point cloud or mesh data, as shown in above tables. In the upper table, we provide two versions of our method, including test-time alignment (TTA) and prealignment (Pre) with a collection of shapes from the trainset data, while in the lower table, only TTA version is provided since the PartNetE dataset does not provide train-set data. From the tables, our method demonstrates its consistency on surpassing the benchmark methods. 
    </div>

    <img src="/assets/img/project_page/2024_partdistill/quantitative_result2.png" alt="Quantitative results" class="img-fluid mx-auto d-block">
    <div class="content" style="margin-top: 1rem">
    Regarding leveraging generative models, if a collection of shapes does not exist, generative models can be employed for shape creation and subsequently used in our method as the knowledge source. From the table above, such approach (second row) achieves competitive results compared to distilling from the train-set data (first row). Furthermore, when a collection of shapes is available, generated data can be employed as supplementary knowledge sources, which can improve the performance (third row).
    </div>
    <br>

    <h3>Acknowledgment</h3>
    <div class="content" style="margin-top: 1rem">
    This work was supported in part by the National Science and Technology Council (NSTC) under grants 112-2221-E-A49-090-MY3, 111-2628-E-A49-025-MY3, 112-2634-F-006-002 and 112-2634-F-A49-007. This work was funded in part by MediaTek and NVIDIA.
    </div>
    <br>
    
    <!-- BibTeX -->
    <h4>BibTeX</h4>
    <div class="bibtex-container">
      <pre id="bibtex">@inproceedings{umam2023partdistill,
      title = {PartDistill: 3D Shape Part Segmentation by Vision-Language Model Distillation},
      author = {Umam, Ardian and Yang, Cheng-Kun and Chen, Min-Hung and Chuang, Jen-Hui and Lin, Yen-Yu},
      booktitle = {IEEE/CVF International Conference on Computer Vision (CVPR)},
      year = {2024},
}</pre>
      <button onclick="copyBibtex()" class="copy-btn">
      <i class="fas fa-copy"></i>
      </button>
    </div>

  </div>

  <!-- Javascript -->
  <script>
    function copyBibtex() {
      var bibtexText = document.getElementById("bibtex").innerText;
      navigator.clipboard.writeText(bibtexText)
      .then(() => {
      // Change the copy icon to a check icon
      var copyBtn = document.querySelector('.copy-btn i');
      copyBtn.classList.remove('fa-copy');
      copyBtn.classList.add('fa-clipboard-check');

      // Optional: Reset the icon back to copy after some time
      setTimeout(() => {
      copyBtn.classList.remove('fa-clipboard-check');
      copyBtn.classList.add('fa-copy');
      }, 2000); // Resets after 2 seconds
      })
      .catch(err => console.error('Error copying BibTeX: ', err));
      }

    const backToTopButton = document.getElementById("back-to-top");
    backToTopButton.addEventListener("click", () => {
      window.scrollTo({ top: 0, behavior: "smooth" });
    });
  </script>

</body>