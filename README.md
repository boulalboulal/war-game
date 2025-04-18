<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Animated Product Display</title>
    <style>
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }
        
        @keyframes rotate {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }
        
        body {
            font-family: 'Arial', sans-serif;
            background-color: #f5f5f5;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
        }
        
        .product-container {
            background: white;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            padding: 30px;
            max-width: 600px;
            text-align: center;
            animation: fadeIn 0.8s ease-out;
            transition: all 0.3s ease;
        }
        
        .product-container:hover {
            box-shadow: 0 15px 40px rgba(0,0,0,0.15);
            transform: translateY(-5px);
        }
        
        .product-image {
            width: 100%;
            max-width: 400px;
            border-radius: 10px;
            transition: all 0.3s ease;
            cursor: pointer;
        }
        
        .product-image:hover {
            animation: pulse 1.5s infinite;
        }
        
        .product-details {
            margin-top: 20px;
        }
        
        h2 {
            color: #333;
            font-size: 28px;
            margin-bottom: 10px;
        }
        
        .specs {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin: 15px 0;
        }
        
        .spec-item {
            background: #f0f0f0;
            padding: 10px 15px;
            border-radius: 8px;
            transition: all 0.3s ease;
        }
        
        .spec-item:hover {
            background: #e0e0e0;
            transform: scale(1.05);
        }
        
        .zoom-icon {
            position: absolute;
            top: 10px;
            right: 10px;
            background: rgba(255,255,255,0.8);
            padding: 5px;
            border-radius: 50%;
            opacity: 0;
            transition: opacity 0.3s ease;
        }
        
        .image-container {
            position: relative;
            display: inline-block;
        }
        
        .image-container:hover .zoom-icon {
            opacity: 1;
            animation: rotate 2s linear infinite;
        }
        
        .cta-button {
            background: linear-gradient(135deg, #6e8efb, #a777e3);
            color: white;
            border: none;
            padding: 12px 30px;
            border-radius: 50px;
            font-size: 16px;
            cursor: pointer;
            margin-top: 20px;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
        }
        
        .cta-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(0,0,0,0.15);
        }
    </style>
</head>
<body>
    <div class="product-container">
        <div class="image-container">
            <img src="IMG_20250418_221253.jpg" 
                 alt="SWICKERS product - Size 4x44x0.6 inches"
                 class="product-image"
                 title="Click to enlarge">
            <div class="zoom-icon">🔍</div>
        </div>
        
        <div class="product-details">
            <h2>SWICKERS</h2>
            
            <div class="specs">
                <div class="spec-item">
                    <strong>Size</strong>
                    <p>4x44x0.6 inches</p>
                </div>
                <div class="spec-item">
                    <strong>Voltage</strong>
                    <p>5:30v</p>
                </div>
            </div>
            
            <button class="cta-button">View Details</button>
        </div>
    </div>

    <script>
        // Add click animation to the product image
        const productImage = document.querySelector('.product-image');
        productImage.addEventListener('click', function() {
            this.style.transform = 'scale(1.8)';
            setTimeout(() => {
                this.style.transform = 'scale(1)';
            }, 300);
        });
        
        // Button click effect
        const ctaButton = document.querySelector('.cta-button');
        ctaButton.addEventListener('click', function() {
            this.textContent = 'Loading...';
            setTimeout(() => {
                this.textContent = 'Details Coming Soon!';
            }, 1000);
        });
    </script>
</body>
</html>
