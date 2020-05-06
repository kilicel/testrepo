<?php
function gradeToPoint($grade){
    $point=0;
    if ($grade == "AA" || $grade == "aa")
    {
        $point = "4";
    }
    elseif ($grade == "BA" || $grade == "ba")
    {
        $point = "3.50";
    }
    elseif ($grade == "BB" || $grade == "bb")
    {
        $point = "3";
    }
    elseif ($grade == "BC" || $grade == "bc")
    {
        $point = "2.50";
    }
    elseif ($grade == "CC" || $grade == "cc")
    {
        $point = "2";
    }
    elseif ($grade == "DC" || $grade == "dc")
    {
        $point = "1.50";
    }
    elseif ($grade == "DD" || $grade == "dd")
    {
        $point = "1";
    }
    elseif ($grade == "FF" || $grade == "ff")
    {
        $point = "0";
    }
    elseif (empty($grade))
    {
        $point = "0";
    }
    return $point;
}

$notlar = array(
    'eski' => array('ortalama' => '2.45', 'toplam_kredi' => '120'),
    'donemdersleri' => array(
        array('yeniders' => '0', 'kredi' => '3', 'yeninot' => 'AA', 'eskinot' => 'CC'),
        array('yeniders' => '1', 'kredi' => '4', 'yeninot' => 'AA', 'eskinot' => ''),
        array('yeniders' => '0', 'kredi' => '3', 'yeninot' => 'AA', 'eskinot' => 'CB'),
        array('yeniders' => '1', 'kredi' => '2', 'yeninot' => 'BA', 'eskinot' => ''),
        array('yeniders' => '1', 'kredi' => '1', 'yeninot' => 'AA', 'eskinot' => '')
    )
);

$totalQPoint = $notlar['eski']['ortalama']*$notlar['eski']['toplam_kredi'];
$donemlikQPoint = 0;

foreach($notlar['donemdersleri'] as $ders) {
    if (!$ders['eskinot']) {
        $notlar['eski']['toplam_kredi'] = $notlar['eski']['toplam_kredi'] + $ders['kredi'];
        print_r($ders['eskinot']);
    }
    else{
        $totalQPoint = $totalQPoint - ($ders['kredi']*(gradeToPoint($ders['eskinot']) - gradeToPoint($ders['yeninot'])));
    }

}

$totalCredits = $notlar['eski']['toplam_kredi']

foreach()

$gpa = $totalQPoint /