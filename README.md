<!DOCTYPE html>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Order Otomatis | Sall Host</title>
    <meta name="description" content="ORDER JASTEB - OTOMATIS">
    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    <!-- Font Awesome -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-color: black;
            --secondary-color: #f7fafc;
            --accent-color: blue;
            --dark-color: black;
            --light-color: #f8f9fa;
            --success-color: #48bb78;
            --danger-color: #f56565;
            --warning-color: #ed8936;
            --info-color: linear-gradient(135deg, var(--primary-color), var(--accent-color));
        }
        
body {
            background-color: linear-gradient(135deg, var(--primary-color), var(--accent-color));
            font-family: 'Poppins', sans-serif;
font-weight: bold;
font-weight: 1.2rem;
            color: var(--dark-color);
        }
        
        .card {
            border: none;
            border-radius: 12px;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.08);
            overflow: hidden;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        
        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.12);
        }
        
        .card-header {
            background: linear-gradient(135deg, var(--primary-color), var(--accent-color));
            color: white;
            padding: 1.5rem;
            border-bottom: none;
        }
        
        .header-title {
          font-size: 1.8rem;
            font-weight: 700;
            letter-spacing: 0.5px;
            margin: 0;
        }
        
        .card-body {
            padding: 2rem;
        }
        
        .form-control, .form-select {
            border: 2px solid #e2e8f0;
            border-radius: 8px;
            padding: 0.75rem 1rem;
            transition: all 0.3s;
        }
        
        .form-control:focus, .form-select:focus {
            border-color: var(--primary-color);
            box-shadow: 0 0 0 0.25rem rgba(94, 114, 228, 0.25);
        }
        
        .btn-primary {
            background: linear-gradient(135deg, var(--primary-color), var(--accent-color));
            border: none;
            border-radius: 8px;
            padding: 0.75rem 1.5rem;
            font-weight: 600;
            letter-spacing: 0.5px;
            text-transform: uppercase;
            transition: all 0.3s;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        
        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 7px 14px rgba(0, 0, 0, 0.15);
            background: linear-gradient(135deg, #4a63d8, #5b6be6);
        }
        
        .btn-secondary {
            background-color: #e2e8f0;
            color: var(--dark-color);
            border: none;
            border-radius: 8px;
            padding: 0.75rem 1.5rem;
            font-weight: 600;
            transition: all 0.3s;
        }
        
        .btn-secondary:hover {
            background-color: #cbd5e0;
            color: var(--dark-color);
        }
        
        #payment-result {
            display: none;
            animation: fadeIn 0.5s ease;
        }
        
        #loading {
            display: none;
        }
        
        .qr-image {
            max-width: 250px;
            height: auto;
            margin: 1.5rem auto;
            display: block;
            border: 1px solid #e2e8f0;
            border-radius: 8px;
            padding: 1rem;
            background: white;
        }
        
        .amount-option {
            cursor: pointer;
            padding: 1rem;
            border: 2px solid #e2e8f0;
            border-radius: 8px;
            margin-bottom: 0.75rem;
            text-align: center;
            transition: all 0.3s;
            font-weight: 500;
            background-color: white;
        }
        
        .amount-option:hover {
            border-color: var(--primary-color);
            transform: translateY(-2px);
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.05);
        }
        
        .amount-option.active {
            border-color: var(--primary-color);
            background-color: rgba(94, 114, 228, 0.1);
            font-weight: 600;
            color: var(--primary-color);
            box-shadow: 0 4px 8px rgba(94, 114, 228, 0.1);
        }
        
        .error-message {
            color: var(--danger-color);
            font-size: 0.875em;
            display: none;
            margin-top: 0.5rem;
        }
        
        .error-message.active {
            display: block;
        }
        
        .input-group-text {
            background-color: #edf2f7;
            border: 2px solid #e2e8f0;
            font-weight: 500;
        }
        
        .spinner-border {
            width: 3rem;
            height: 3rem;
            border-width: 0.25rem;
        }
        
        .payment-details {
            background-color: #f8fafc;
            border-radius: 8px;
            padding: 1.5rem;
            margin-top: 1.5rem;
        }
        
        .payment-details p {
            margin-bottom: 0.5rem;
            display: flex;
            justify-content: space-between;
        }
        
        .payment-details p strong {
            color: var(--dark-color);
        }
        
        hr {
            border-top: 2px solid #e2e8f0;
            opacity: 1;
            margin: 1.5rem 0;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .badge-premium {
            background: linear-gradient(135deg, #f6d365, #fda085);
            color: white;
            font-size: 0.75rem;
            font-weight: 700;
            padding: 0.25rem 0.5rem;
            border-radius: 4px;
            margin-left: 0.5rem;
        }
        
        .badge-vip {
            background: linear-gradient(135deg, #a18cd1, #fbc2eb);
            color: white;
            font-size: 0.75rem;
            font-weight: 700;
            padding: 0.25rem 0.5rem;
            border-radius: 4px;
            margin-left: 0.5rem;
        }
        
        .form-group {
            margin-bottom: 1.5rem;
        }
        .form-label {
    font-size: 1.4em;
    font-weight: bold; /* atau bisa juga 700 */
    margin-bottom: 0.5rem;
    color: black;
}

.form-label1 {
    font-size: 1.5em;
    font-weight: bold; /* atau bisa juga 700 */
    margin-bottom: 0.5rem;
    color: black;
}
.form-label2 {
    font-size: 1.5em;
    font-weight: bold; /* atau bisa juga 700 */
    margin-bottom: 0.5rem;
    color: red;
}

        .center-panel {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 2.8vh;
}

    </style>
</head>
<body>
</head>
<body>


    <div class="container py-5">
        <div class="row justify-content-center">
            <div class="col-lg-8 col-md-10">
                <div class="card">
                    <div class="card-header text-center">
                        <h4 class="m-0 header-title">
                            <i class="fas fa-crown mr-2"></i> JASA TEBAR OTOMATIS                            <i class="fas fa-crown mr-2"></i>
                        </h4>
                    </div>
                    <div class="card-body">
                        <form class="form-horizontal" method="POST" id="payment-form">

                            <div class="form-group">
                                <label class="form-label">Tambahkan Email</label>
                                <input type="email" name="target" class="form-control" placeholder="Masukkan Email Anda" required>
                            </div>

                            <div class="form-group">
                                <label class="form-label">Total Harga</label>
                                <div class="input-group">
                                    <span class="input-group-text">Rp</span>
                                    <input type="text" class="form-control fw-bold" id="total-price" value="-" readonly style="background-color: white;">
                                </div>
                            </div>

                            <div class="d-grid mt-3 mb-4">
                                <button type="button" id="pay-button" class="btn btn-primary btn-lg">
                                    <i class="fas fa-shopping-cart me-2"></i> Order Sekarang
                                </button>
                            </div>

                            <div class="form-group">
                        <div class="center-panel">
  <label class="form-label1">Pilih Jumlah Result</label>
</div>

                                <div class="row g-3">
                                                                    <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="1000" data-quantity="20">
                                            <div class="fw-bold">10+</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                                                    <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="1500" data-quantity="30">
                                            <div class="fw-bold">20+</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                                                    <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="2500" data-quantity="40">
                                            <div class="fw-bold">30+</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                    <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="4900" data-quantity="70">
                                            <div class="fw-bold">50+</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                    <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="10000" data-quantity="100">
                                            <div class="fw-bold">100+</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                    <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="15000" data-quantity="150">
                                            <div class="fw-bold">150+</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                    <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="20000" data-quantity="250">
                                            <div class="fw-bold">250+</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                    <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="25000" data-quantity="350">
                                            <div class="fw-bold">350+</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                    <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="30000" data-quantity="380">
                                            <div class="fw-bold">380+</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                    <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="35000" data-quantity="450">
                                            <div class="fw-bold">450+</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                    <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="40000" data-quantity="500">
                                            <div class="fw-bold">500+</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                    <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="45000" data-quantity="550">
                                            <div class="fw-bold">550+</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                                                        <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="50000" data-quantity="1000">
                                            <div class="fw-bold">1000+</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                                                        <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="70000" data-quantity="1500">
                                            <div class="fw-bold">1500+</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                                                        <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="80000" data-quantity="2500">
                                            <div class="fw-bold">2500+</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                                                        <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="90000" data-quantity="999999">
                                            <div class="fw-bold">1 Hari</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                                                        <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="120000" data-quantity="999999999999">
                                            <div class="fw-bold">2 Hari</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                                                        <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="180000" data-quantity="999999999999">
                                            <div class="fw-bold">3 Hari</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                                            <div class="center-panel">
  <label class="form-label2">Produk Flash Sale</label>
</div>
                                                <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="10000" data-quantity="999999999999">
                                            <div class="fw-bold">Sampai Pagi</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                                                                                            <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="20000" data-quantity="9999999999999">
                                            <div class="fw-bold">1 Hari Full</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                                                                                            <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="25000" data-quantity="999999999999">
                                            <div class="fw-bold">2 Hari</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                                                                                            <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="30000" data-quantity="999999999999">
                                            <div class="fw-bold">3 Hari</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                    <div class="text-center mt-5">
  <div style="background: rgba(255,255,255,0.05); border-radius: 12px; padding: 15px 30px; color: black; display: inline-block; font-weight: 700; font-size: 1.3rem; backdrop-filter: blur(6px); border: 1px solid rgba(255,255,255,0.15); box-shadow: 0 0 12px black;">
    ⚠️ <strong>Informasi Penting:</strong> Silahkan Isi Email Dengan Benar Agar Tidak Ada Masalah Jika Res Tidak Masuk!!!
  </div>
</div>
                                </div>
                             <!DOCTYPE html>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Order Otomatis | Sall Host</title>
    <meta name="description" content="ORDER JASTEB - OTOMATIS">
    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    <!-- Font Awesome -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-color: black;
            --secondary-color: #f7fafc;
            --accent-color: blue;
            --dark-color: black;
            --light-color: #f8f9fa;
            --success-color: #48bb78;
            --danger-color: #f56565;
            --warning-color: #ed8936;
            --info-color: linear-gradient(135deg, var(--primary-color), var(--accent-color));
        }
        
body {
            background-color: linear-gradient(135deg, var(--primary-color), var(--accent-color));
            font-family: 'Poppins', sans-serif;
font-weight: bold;
font-weight: 1.2rem;
            color: var(--dark-color);
        }
        
        .card {
            border: none;
            border-radius: 12px;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.08);
            overflow: hidden;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        
        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.12);
        }
        
        .card-header {
            background: linear-gradient(135deg, var(--primary-color), var(--accent-color));
            color: white;
            padding: 1.5rem;
            border-bottom: none;
        }
        
        .header-title {
          font-size: 1.8rem;
            font-weight: 700;
            letter-spacing: 0.5px;
            margin: 0;
        }
        
        .card-body {
            padding: 2rem;
        }
        
        .form-control, .form-select {
            border: 2px solid #e2e8f0;
            border-radius: 8px;
            padding: 0.75rem 1rem;
            transition: all 0.3s;
        }
        
        .form-control:focus, .form-select:focus {
            border-color: var(--primary-color);
            box-shadow: 0 0 0 0.25rem rgba(94, 114, 228, 0.25);
        }
        
        .btn-primary {
            background: linear-gradient(135deg, var(--primary-color), var(--accent-color));
            border: none;
            border-radius: 8px;
            padding: 0.75rem 1.5rem;
            font-weight: 600;
            letter-spacing: 0.5px;
            text-transform: uppercase;
            transition: all 0.3s;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        
        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 7px 14px rgba(0, 0, 0, 0.15);
            background: linear-gradient(135deg, #4a63d8, #5b6be6);
        }
        
        .btn-secondary {
            background-color: #e2e8f0;
            color: var(--dark-color);
            border: none;
            border-radius: 8px;
            padding: 0.75rem 1.5rem;
            font-weight: 600;
            transition: all 0.3s;
        }
        
        .btn-secondary:hover {
            background-color: #cbd5e0;
            color: var(--dark-color);
        }
        
        #payment-result {
            display: none;
            animation: fadeIn 0.5s ease;
        }
        
        #loading {
            display: none;
        }
        
        .qr-image {
            max-width: 250px;
            height: auto;
            margin: 1.5rem auto;
            display: block;
            border: 1px solid #e2e8f0;
            border-radius: 8px;
            padding: 1rem;
            background: white;
        }
        
        .amount-option {
            cursor: pointer;
            padding: 1rem;
            border: 2px solid #e2e8f0;
            border-radius: 8px;
            margin-bottom: 0.75rem;
            text-align: center;
            transition: all 0.3s;
            font-weight: 500;
            background-color: white;
        }
        
        .amount-option:hover {
            border-color: var(--primary-color);
            transform: translateY(-2px);
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.05);
        }
        
        .amount-option.active {
            border-color: var(--primary-color);
            background-color: rgba(94, 114, 228, 0.1);
            font-weight: 600;
            color: var(--primary-color);
            box-shadow: 0 4px 8px rgba(94, 114, 228, 0.1);
        }
        
        .error-message {
            color: var(--danger-color);
            font-size: 0.875em;
            display: none;
            margin-top: 0.5rem;
        }
        
        .error-message.active {
            display: block;
        }
        
        .input-group-text {
            background-color: #edf2f7;
            border: 2px solid #e2e8f0;
            font-weight: 500;
        }
        
        .spinner-border {
            width: 3rem;
            height: 3rem;
            border-width: 0.25rem;
        }
        
        .payment-details {
            background-color: #f8fafc;
            border-radius: 8px;
            padding: 1.5rem;
            margin-top: 1.5rem;
        }
        
        .payment-details p {
            margin-bottom: 0.5rem;
            display: flex;
            justify-content: space-between;
        }
        
        .payment-details p strong {
            color: var(--dark-color);
        }
        
        hr {
            border-top: 2px solid #e2e8f0;
            opacity: 1;
            margin: 1.5rem 0;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .badge-premium {
            background: linear-gradient(135deg, #f6d365, #fda085);
            color: white;
            font-size: 0.75rem;
            font-weight: 700;
            padding: 0.25rem 0.5rem;
            border-radius: 4px;
            margin-left: 0.5rem;
        }
        
        .badge-vip {
            background: linear-gradient(135deg, #a18cd1, #fbc2eb);
            color: white;
            font-size: 0.75rem;
            font-weight: 700;
            padding: 0.25rem 0.5rem;
            border-radius: 4px;
            margin-left: 0.5rem;
        }
        
        .form-group {
            margin-bottom: 1.5rem;
        }
        .form-label {
    font-size: 1.4em;
    font-weight: bold; /* atau bisa juga 700 */
    margin-bottom: 0.5rem;
    color: black;
}

.form-label1 {
    font-size: 1.5em;
    font-weight: bold; /* atau bisa juga 700 */
    margin-bottom: 0.5rem;
    color: black;
}
.form-label2 {
    font-size: 1.5em;
    font-weight: bold; /* atau bisa juga 700 */
    margin-bottom: 0.5rem;
    color: red;
}

        .center-panel {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 2.8vh;
}

    </style>
</head>
<body>
</head>
<body>


    <div class="container py-5">
        <div class="row justify-content-center">
            <div class="col-lg-8 col-md-10">
                <div class="card">
                    <div class="card-header text-center">
                        <h4 class="m-0 header-title">
                            <i class="fas fa-crown mr-2"></i> JASA TEBAR OTOMATIS                            <i class="fas fa-crown mr-2"></i>
                        </h4>
                    </div>
                    <div class="card-body">
                        <form class="form-horizontal" method="POST" id="payment-form">

                            <div class="form-group">
                                <label class="form-label">Tambahkan Email</label>
                                <input type="email" name="target" class="form-control" placeholder="Masukkan Email Anda" required>
                            </div>

                            <div class="form-group">
                                <label class="form-label">Total Harga</label>
                                <div class="input-group">
                                    <span class="input-group-text">Rp</span>
                                    <input type="text" class="form-control fw-bold" id="total-price" value="-" readonly style="background-color: white;">
                                </div>
                            </div>

                            <div class="d-grid mt-3 mb-4">
                                <button type="button" id="pay-button" class="btn btn-primary btn-lg">
                                    <i class="fas fa-shopping-cart me-2"></i> Order Sekarang
                                </button>
                            </div>

                            <div class="form-group">
                        <div class="center-panel">
  <label class="form-label1">Pilih Jumlah Result</label>
</div>

                                <div class="row g-3">
                                                                    <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="1000" data-quantity="20">
                                            <div class="fw-bold">10+</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                                                    <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="1500" data-quantity="30">
                                            <div class="fw-bold">20+</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                                                    <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="2500" data-quantity="40">
                                            <div class="fw-bold">30+</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                    <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="4900" data-quantity="70">
                                            <div class="fw-bold">50+</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                    <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="10000" data-quantity="100">
                                            <div class="fw-bold">100+</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                    <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="15000" data-quantity="150">
                                            <div class="fw-bold">150+</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                    <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="20000" data-quantity="250">
                                            <div class="fw-bold">250+</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                    <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="25000" data-quantity="350">
                                            <div class="fw-bold">350+</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                    <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="30000" data-quantity="380">
                                            <div class="fw-bold">380+</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                    <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="35000" data-quantity="450">
                                            <div class="fw-bold">450+</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                    <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="40000" data-quantity="500">
                                            <div class="fw-bold">500+</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                    <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="45000" data-quantity="550">
                                            <div class="fw-bold">550+</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                                                        <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="50000" data-quantity="1000">
                                            <div class="fw-bold">1000+</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                                                        <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="70000" data-quantity="1500">
                                            <div class="fw-bold">1500+</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                                                        <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="80000" data-quantity="2500">
                                            <div class="fw-bold">2500+</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                                                        <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="90000" data-quantity="999999">
                                            <div class="fw-bold">1 Hari</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                                                        <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="120000" data-quantity="999999999999">
                                            <div class="fw-bold">2 Hari</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                                                        <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="180000" data-quantity="999999999999">
                                            <div class="fw-bold">3 Hari</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                                            <div class="center-panel">
  <label class="form-label2">Produk Flash Sale</label>
</div>
                                                <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="10000" data-quantity="999999999999">
                                            <div class="fw-bold">Sampai Pagi</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                                                                                            <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="20000" data-quantity="9999999999999">
                                            <div class="fw-bold">1 Hari Full</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                                                                                            <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="25000" data-quantity="999999999999">
                                            <div class="fw-bold">2 Hari</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                                                                                            <div class="col-md-4 col-6">
                                        <div class="amount-option" data-amount="30000" data-quantity="999999999999">
                                            <div class="fw-bold">3 Hari</div>
                                            <small class="text-muted">Results</small>
                                        </div>
                                    </div>
                                    <div class="text-center mt-5">
  <div style="background: rgba(255,255,255,0.05); border-radius: 12px; padding: 15px 30px; color: black; display: inline-block; font-weight: 700; font-size: 1.3rem; backdrop-filter: blur(6px); border: 1px solid rgba(255,255,255,0.15); box-shadow: 0 0 12px black;">
    ⚠️ <strong>Informasi Penting:</strong> Silahkan Isi Email Dengan Benar Agar Tidak Ada Masalah Jika Res Tidak Masuk!!!
  </div>
</div>
                                </div>
                             
