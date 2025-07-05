<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>CK Detection Strip – Color-Based Blood Test</title>
  <style>
    body {
      font-family: Arial, sans-serif;
    }
    #canvas, #graphCanvas {
      display: block;
      margin-top: 15px;
      max-width: 100%;
      background: #fff;
      border: 1px solid #ccc;
    }
    #resultBox {
      font-size: 18px;
      margin-top: 15px;
      padding: 10px;
      border: 2px solid #333;
      border-radius: 8px;
      max-width: 400px;
      background-color: #f2f2f2;
    }
  </style>
</head>
<body>
  <header style="background: url('https://iq-laboratory.com/wp-content/uploads/2021/04/laboratory-design.jpg') center/cover no-repeat; padding: 40px 20px; text-align: center; color: black;">
  <h1 style="margin: 0; font-size: 36px;">CK Detection Strip</h1>
  <p style="margin: 10px 0 0; font-size: 20px;">Color-Based Diagnostic for Creatine Kinase Activity</p>
</header>

  <nav style="background-color: #1b3c5d; padding: 10px; position: relative;">
  <div style="display: flex; justify-content: space-between; align-items: center;">
    <div style="color: white; font-weight: bold; font-size: 20px;">☰</div>
    <div id="menu" style="display: none; flex-direction: column; background-color: #1b3c5d; position: absolute; top: 45px; right: 10px; width: 200px;">
      <a href="#home" style="color: white; padding: 10px; text-decoration: none; border-bottom: 1px solid #fff;">Home</a>
      <a href="#how" style="color: white; padding: 10px; text-decoration: none; border-bottom: 1px solid #fff;">How It Works</a>
      <a href="#image" style="color: white; padding: 10px; text-decoration: none; border-bottom: 1px solid #fff;">Image Analysis</a>
      <a href="#research" style="color: white; padding: 10px; text-decoration: none; border-bottom: 1px solid #fff;">Research</a>
      <a href="#contact" style="color: white; padding: 10px; text-decoration: none;">Contact</a>
    </div>
  </div>
</nav>
<script>
  const menuIcon = document.querySelector('nav div');
  const menu = document.getElementById('menu');
  menuIcon.addEventListener('click', () => {
    menu.style.display = menu.style.display === 'flex' ? 'none' : 'flex';
  });
</script>

  <section id="home">
    <h2>Home</h2>
    <p>This project introduces a low-cost colorimetric strip designed to detect Creatine Kinase (CK) activity in human blood. CK levels are crucial indicators in diagnosing a variety of conditions, such as myocardial infarction, muscle dystrophies, and rhabdomyolysis. Traditional laboratory-based tests can be expensive, time-consuming, and inaccessible in remote or low-resource settings.</p>
    <p>Our portable, strip-based approach bridges this gap by providing a rapid, user-friendly, and cost-effective solution. With the aid of a smartphone camera and this web platform, color intensity from the test strip is quantified and converted into clinically relevant CK levels. This eliminates the need for advanced laboratory infrastructure while ensuring accuracy and reproducibility.</p>
    <p>This platform supports public health outreach, on-field diagnostics, and patient self-monitoring. It can be integrated into mobile health strategies, enabling large-scale screening in communities and improving access to early diagnosis and treatment. The technology behind this innovation merges biochemistry, digital image processing, and biomedical engineering into a single, seamless solution.</p>
  </section>

  <section id="how">
    <h2>How It Works</h2>
    <h3>Traditional Method</h3>
    <p>Traditionally, CK activity is measured in laboratories using automated analyzers which rely on spectrophotometry. The typical reaction used in standard biochemical CK assay is:</p>
    <p style="font-size: 20px; color: red;"><strong>Creatine Phosphate + ADP ⇌ Creatine + ATP</strong></p>
    <p>Then, ATP reacts in a coupled enzyme system producing a measurable change in absorbance:</p>
    <p style="font-size: 20px; color: red;"><strong>ATP + Glucose → ADP + Glucose-6-Phosphate (via Hexokinase)</strong><br><strong>Glucose-6-Phosphate + NADP⁺ → 6-Phosphogluconate + NADPH + H⁺ (via G6PD)</strong></p>
    <p>The amount of NADPH formed is proportional to CK activity and is read at 340nm absorbance.</p>

    <h3>Proposed Innovation:</h3>
    <p>This project introduces a novel visual detection strip that relies on a simplified version of the CK enzymatic reaction. The innovative approach avoids the need for spectrophotometric instrumentation by detecting color changes induced by the enzymatic activity on the strip. The key chemical reaction remains:</p>
    <p style="font-size: 20px; color: red;"><strong>Creatine Phosphate + ADP → Creatine + ATP</strong></p>
    <p>The generated ATP triggers a pH-sensitive or colorimetric indicator embedded in the strip, resulting in a visible color change that can be captured by a smartphone camera. The digital image is then analyzed for grayscale intensity, which correlates with CK concentration.</p>
    <p><strong>Steps in the New Method:</strong></p>
    <ol>
      <li>A drop of blood (5–10 µL) is applied to the pre-coated strip, which contains immobilized Creatine Phosphate and ADP substrates, and a pH-sensitive dye.</li>
      <li>The CK enzyme in the blood catalyzes the reaction:<br><strong style="color: red; font-size: 18px;">Creatine Phosphate + ADP → Creatine + ATP</strong><br>This reaction typically occurs within 30–60 seconds at room temperature.</li>
      <li>The ATP produced reacts with the embedded colorimetric indicator, leading to a visible color change. Higher CK levels yield faster and darker color development. Reaction time: 2–3 minutes.</li>
      <li>The user captures the image of the strip using their mobile phone.</li>
      <li>The uploaded image is processed via this web platform.</li>
      <li>Software converts the image to grayscale and calculates the average pixel intensity. A lower grayscale value indicates a darker color, which correlates with a higher CK concentration.</li>
      <li>CK level is estimated and classified (Low / Normal / High).</li>
      <li>Results are shown graphically and numerically for easy interpretation.</li>
    </ol>
    <p>This innovation improves accessibility, affordability, and allows quick CK screening in low-resource or rural environments.</p>
  </section>

  <section id="image">
    <h2>Image Analysis</h2>
    <input type="file" id="imageUpload" accept="image/*">
    <canvas id="canvas"></canvas>
    <canvas id="graphCanvas"></canvas>
    <div id="resultBox"></div>
    <button id="downloadBtn">Download PDF Report</button>
  </section>

  <section id="research">
    <h2>Research & Applications</h2>
    <p><strong>Normal CK range:</strong> 20 to 150 U/L</p>
    <p>CK levels are used in diagnosing muscular and heart-related conditions. Elevated CK can indicate muscle damage, inflammation, or neuromuscular disorders.</p>
    <p>Creatine kinase exists in different isoforms: CK-MM (skeletal muscle), CK-MB (heart muscle), and CK-BB (brain). This differentiation helps in pinpointing the location of tissue damage. For instance, high CK-MB levels are indicative of myocardial infarction, while CK-BB might be elevated in certain brain injuries or strokes.</p>
    <p>Factors like intense exercise, intramuscular injections, or even certain medications can transiently raise CK levels. Therefore, interpretation should always consider the patient's history and symptoms.</p>
    <p>Ongoing research is looking at portable CK tests for field use, especially in athletes, military personnel, and post-operative care. Early detection of muscle breakdown or cardiac stress can greatly improve treatment outcomes and reduce recovery times.</p>
    <p>Recent innovations in bioengineering and mobile health diagnostics allow for non-invasive, real-time CK monitoring using colorimetric principles and digital imaging. Such tools help in detecting and tracking neuromuscular disorders, improving care in rural or low-resource settings.</p>
    <p>Additionally, longitudinal CK tracking helps in managing chronic diseases such as muscular dystrophies and autoimmune myopathies. Researchers are integrating this with wearable tech and cloud-based analytics for proactive health insights.</p>
    <table style="width: 100%; border-collapse: collapse; margin: 20px 0;">
      <thead>
        <tr style="background-color: #f2f2f2;">
          <th style="border: 1px solid #ccc; padding: 8px;">Disorder</th>
          <th style="border: 1px solid #ccc; padding: 8px;">Typical CK Level (U/L)</th>
          <th style="border: 1px solid #ccc; padding: 8px;">Remarks</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td style="border: 1px solid #ccc; padding: 8px;">Normal</td>
          <td style="border: 1px solid #ccc; padding: 8px;">20–150</td>
          <td style="border: 1px solid #ccc; padding: 8px;">Healthy range</td>
        </tr>
        <tr>
          <td style="border: 1px solid #ccc; padding: 8px;">Duchenne Muscular Dystrophy</td>
          <td style="border: 1px solid #ccc; padding: 8px;">>10,000</td>
          <td style="border: 1px solid #ccc; padding: 8px;">Very high in early stages</td>
        </tr>
        <tr>
          <td style="border: 1px solid #ccc; padding: 8px;">Myocardial Infarction</td>
          <td style="border: 1px solid #ccc; padding: 8px;">>200–1,000 (CK-MB)</td>
          <td style="border: 1px solid #ccc; padding: 8px;">Rises after heart attack</td>
        </tr>
        <tr>
          <td style="border: 1px solid #ccc; padding: 8px;">Rhabdomyolysis</td>
          <td style="border: 1px solid #ccc; padding: 8px;">>100,000</td>
          <td style="border: 1px solid #ccc; padding: 8px;">Severe muscle injury</td>
        </tr>
        <tr>
          <td style="border: 1px solid #ccc; padding: 8px;">Inflammatory Myopathies</td>
          <td style="border: 1px solid #ccc; padding: 8px;">500–10,000</td>
          <td style="border: 1px solid #ccc; padding: 8px;">Chronic inflammation</td>
        </tr>
        <tr>
          <td style="border: 1px solid #ccc; padding: 8px;">Seizures/Stroke</td>
          <td style="border: 1px solid #ccc; padding: 8px;">Mild to Moderate Elevation</td>
          <td style="border: 1px solid #ccc; padding: 8px;">Short-term spike</td>
        </tr>
      </tbody>
    </table>
  </section>

  <section id="contact">
    <h2>Contact</h2>
    <p>Project by: <strong>Mr. ASHOK D</strong></p>
    <p>Email: <a href="mailto:ashokdeivasigamanip@gmail.com">ashokdeivasigamanip@gmail.com</a></p>
    <p>Phone: <a href="tel:+918438698083">8438698083</a></p>
    <hr>
    <p>Project Member: <strong>Ms. Jeevitha M</strong></p>
    <p>Email: <a href="mailto:jeevimurugan1506@gmail.com">jeevimurugan1506@gmail.com</a></p>
    <p>Phone: <a href="tel:+919787815062">9787815062</a></p>
    <hr>
    <p>Project Member: <strong>Ms. Sahiba Jahan M</strong></p>
    <p>Email: <a href="mailto:sahiba8444@gmail.com">sahiba8444@gmail.com</a></p>
    <p>Phone: <a href="tel:+917373511110">7373511110</a></p>
    <hr>
    <p>Project Member: <strong>Mr. Vijayakumar V</strong></p>
    <p>Email: <a href="mailto:ponvid123@gmail.com">ponvid123@gmail.com</a></p>
    <p>Phone: <a href="tel:+918015709365">8015709365</a></p>
    <p>Institution: Biomedical Engineering Department, Sri Shakthi Institute of Engineering and Technology</p>
    <p>Location: Coimbatore, Tamil Nadu, India</p>
  </section>

  <footer>
    <p>&copy; 2025 CK Detection Strip | Biomedical Engineering Project</p>
  </footer>

  <script>
    const imageUpload = document.getElementById('imageUpload');
    const canvas = document.getElementById('canvas');
    const graphCanvas = document.getElementById('graphCanvas');
    const ctx = canvas.getContext('2d');
    const graphCtx = graphCanvas.getContext('2d');

    imageUpload.addEventListener('change', function (e) {
      const file = e.target.files[0];
      if (!file) return;

      const img = new Image();
      const reader = new FileReader();

      reader.onload = function (evt) {
        img.src = evt.target.result;
      };

      img.onload = function () {
        canvas.width = img.width;
        canvas.height = img.height;
        ctx.drawImage(img, 0, 0);

        const imageData = ctx.getImageData(0, 0, canvas.width, canvas.height);
        const data = imageData.data;
        const grayscale = [];

        for (let i = 0; i < data.length; i += 4) {
          const avg = (data[i] + data[i + 1] + data[i + 2]) / 3;
          grayscale.push(avg);
        }

        const avgGray = grayscale.reduce((a, b) => a + b, 0) / grayscale.length;
        const ckLevel = Math.round((255 - avgGray) * 0.8);

        let status = '';
        if (ckLevel < 20) status = 'Low CK Level';
        else if (ckLevel <= 150) status = 'Normal CK Level';
        else status = 'High CK Level';

        let color = '';
        if (ckLevel < 20) color = 'blue';
        else if (ckLevel <= 150) color = 'green';
        else color = 'crimson';

        document.getElementById('resultBox').innerHTML = `<strong style="color:${color};">Estimated CK Level:</strong> <span style="color:${color};">${ckLevel} U/L</span><br><strong style="color:${color};">Status:</strong> <span style="color:${color};">${status}</span>`;

        graphCanvas.width = 500;
        graphCanvas.height = 150;
        graphCtx.clearRect(0, 0, graphCanvas.width, graphCanvas.height);
        graphCtx.beginPath();
        for (let i = 0; i < grayscale.length; i++) {
        const y = graphCanvas.height - (grayscale[i] / 255) * graphCanvas.height;
        graphCtx.beginPath();
        graphCtx.arc(i, y, 1.5, 0, 2 * Math.PI);
        graphCtx.fillStyle = color;
        graphCtx.fill();
          if (i === 0) graphCtx.moveTo(i, y);
          else graphCtx.lineTo(i, y);
        }
        graphCtx.strokeStyle = color;
        graphCtx.lineWidth = 1;
        graphCtx.stroke();

        graphCtx.save();
        graphCtx.fillStyle = '#000';
        graphCtx.font = '12px Arial';
        graphCtx.fillStyle = color;
graphCtx.fillText('Pixel Position →', 10, graphCanvas.height - 10);
        graphCtx.translate(10, graphCanvas.height / 2);
        graphCtx.rotate(-Math.PI / 2);
        graphCtx.fillStyle = color;
graphCtx.fillText('Grayscale Intensity ↑', 0, 0);
        graphCtx.restore();
      };

      reader.readAsDataURL(file);
    });
  </script>
</body>
</html>
