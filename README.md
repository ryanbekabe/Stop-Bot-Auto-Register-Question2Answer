# Stop-Bot-Auto-Register-Question2Answer
Mengcekal bot yang otomatis mendaftar akun pada Question2Answer

![Anti Bot Register Question2Answer](https://github.com/ryanbekabe/Stop-Bot-Auto-Register-Question2Answer/raw/main/Stop-Bot-Auto-Register-Question2Answer.png)

Perlu diketahui, bot auto register yang otomatis mendaftarkan akun ke website yang berbasis Question2Answer ini menggunakan method POST, berikut contohnya:

```git
HTTP headers:
POST
/index.php?qa=register&to=index.php

Request body:
handle=JasminK74102&password=_ca2BsI2kLQ4X&email=lucky77.picard@zohomail.com&doregister=1&code=0-1629268503-3001e6fc82f1d39877f0172d367420bc41c47a3f&g-recaptcha-response=

Request body:
handle=CarolHedberg&password=NONRn7%21gS20&email=carol_hedberg@leather.sfxmailbox.com&doregisterbkb=0&doregister_modif=1&code=0-1629612433-d267c0065f3d869ad2e40250ae52b1ad3aefb003&g-recaptcha-response=03AGdBq24bsBlWFORCBUFmQlCG8JHj7kX-bAfjhcjlD10j29pbcoqg6Fj7oXx4orj4WYoCAAirxjayjAHest0S_5vi0tUtUv_gd6PAZHDg0NdteFkT8KQOg2lhCVtwev1zQ8qH5ItRxD5jXXohXdvSLJFR9aNfW6qfGJbtIp9r8cyGTMR_ks0GS-YJ2hTZBN_G1A66Lhq3-ZsGvX7_maLEAN-lnysVjBg36zdTcLyPHYzix1UYXhk3-Ga0pcvZ3PFNWzTfZk_JNQGy5ivQ5KXEm_rabaHXp4SwNxCq05hk2yOWcJHx7Ukt1bAN_E21yqaxDwbrZcfRWeyTbyNEtTt4oQUQGJkPc5v6etByoEYPAaLMJVTjCBb0CpqZkJxIjPWfwUv6quDKfgrvpdT1RGz95Hu4GqzqoQrITfR-7hhcjxAhIxvDubhus4mqzxF_1XsWD0YrXeMd5IJdolq8ye1i52A6jFWFyAoEIDF0szj7bPSEcNxdv1Q02DZAdhWfZrj2dvB6OYFaDiCgJzkkx9ATfUL4uazS9dWmCg

Request body:
emailhandle=rosalindavalos80@over.nymega.com&password=L-EQif352&code=0-1629712909-d05c10bce598a807429a11545d816033e148d894&dologin=Masuk&g-recaptcha-response=03AGdBq27Hu4R6S5JN6sCOwWnGDPExj7hLIaaCVRrwWPQryaRShjn8gj8ZIMWMscPBDS650UGYS1tpt2Lyc-lDnSy_tUDQh4NPezBhtgqLT0RHmraVroTYPG4k_HERr3KylTu9rH46TDbwwvPksmwNYiCAnGw1R6m5cBXNmgUmzXumisy4y1CM-KMKRL4Hber1av-ukVK0wL4syDXELiPwPtuyRMm-ivTN4nrwBqzfGc78RnDtAqBWqASE5D0q-JODWAAPsqj6JHO-Gp-1vAjU3gzf9Gsv1UrwAkPqxPVJtctBhQTcc33dn0YHEyS6OidStgl2LrnBRT_y8SLYkRO0oiaTqMyxVXY_NLv6YqSKYdljhwdHpT-ADvpXXm8fmaVeyOkUrqq6DV7IyLbe-LhrYiPG_gofvNJHW1EpaY0BAqyzkgKT4NigWekelXJ1jpuQXHAHnpKlalusowgJvSQW4h5KssRSw0R5KPiW3Xs7hUF1rN0KgZewROJKjjANsj0tF-8G60-VqiTZCmTTJMqBWwWnlArvuYXqmw
```

Maka untuk mengatasinya, diperlukan modifikasi field textbox yang ada pada file qa-include/pages/register.php, yakni dengan merubah pada "$qa_content['form'] = array", yakni pada "hidden" dengan nama textbox "'doregister' => '1'", rubah dengan nama lain, misal "doregister_modif".

Adapun "doregister" yang akan digunakan untuk mendaftar yang sebenarnya kita letakkan pada "'fields' => array", pada "'handle' => array", misal saya beri nama "doregisterbkb".

Jadi, field handle dengan nama "doregisterbkb" tersebut harus dirubah terlebih dahulu namanya supaya proses pendaftaran user baru bisa dilakukan. Untuk merubahnya dilakukan manipulasi dengan DOM, yang diletakkan pada qa-include/qa-theme-base.php, yang saya letakkan JavaScript DOM pada "public function main()".

Sejauh ini, reCAPTCHA v2 dari Google masih bisa ditembus, dan sedangkan dengan manupulasi DOM ini tidak bisa ditembus.



Regard,

Riyan Hidayat Samosir


Palangka, Raya - Indonesia - 23 Agustus 2021. hanyajasa.com.
