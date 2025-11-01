# Design-of-FIR-Filters-using-hanning-window

# DESIGN OF FIR DIGITAL FILTER 

# AIM: 
          
  To generate design of low pass FIR digital filter using SCILAB 

# APPARATUS REQUIRED: 

  PC Installed with SCILAB 

# PROGRAM 


clc;
clear;
close;

// FIR Low Pass Filter Design using Fourier Series Method
// using Hanning Window

// Step 1: Input specifications
M = input("Enter the Odd Filter Length = ");          // e.g., 21
Wc = input("Enter the Digital Cutoff Frequency (in radians) = ");  // e.g., 0.4*%pi

alpha = (M - 1) / 2;    // Center index

// Step 2: Compute ideal impulse response (sinc function)
for n = 1:M
    if (n == alpha + 1) then
        hd(n) = Wc / %pi;   // center value (sinc(0))
    else
        hd(n) = sin(Wc * ((n - 1) - alpha)) / (((n - 1) - alpha) * %pi);
    end
end

// Step 3: Define Hanning Window
for n = 1:M
    W(n) = 0.5 - (0.5 * cos((2 * %pi * (n - 1)) / (M - 1)));
end

// Step 4: Apply window to impulse response
h = hd .* W;
disp(h, "Filter Coefficients are:");

// Step 5: Compute Frequency Response
[hzm, fr] = frmag(h, 256);  // 256-point frequency response

// Step 6: Plot magnitude and magnitude (dB)
subplot(2,1,1);
plot(2*fr, hzm);
xlabel("Normalized Digital Frequency (×π rad/sample)");
ylabel("Magnitude");
title("Frequency Response of FIR LPF using Hanning Window");

subplot(2,1,2);
hzm_dB = 20 * log10(hzm);
plot(2*fr, hzm_dB);
xlabel("Normalized Digital Frequency (×π rad/sample)");
ylabel("Magnitude (dB)");
title("Frequency Response of FIR LPF using Hanning Window (in dB)");


# OUTPUT
<img width="1138" height="634" alt="image" src="https://github.com/user-attachments/assets/628070a5-313e-4c4f-a133-7399fc2b0cb7" />

# RESULT
Thus , generate design of low pass FIR digital filter using SCILAB are verified.
