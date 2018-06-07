# timer-countdown
```
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8" />
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <title>Timer</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
</head>
<body>

  <div id="timer">
    <ul class="list-unstyled">
      <li><span id="days">00</span> Días</li>
      <li><span id="hours">00</span> Horas</li>
      <li><span id="minutes">00</span> Minutos</li>
      <li><span id="seconds">00</span> Segundos</li>
    </ul>
  </div>

  <script>
    var $timer, $countDown, $day, $hour, $minute, $second, $x;
    $timer = document.getElementById('timer');
    if ($timer !== null) {
      $second = 1000;
      $minute = $second * 60;
      $hour = $minute * 60;
      $day = $hour * 24;
      $countDown = new Date('Jun 30, 2018 00:00:00').getTime();
      $x = setInterval((function() {
        var $days, $hours, $minutes, $seconds, $distance, $now;
        $now = (new Date).getTime();
        $distance = $countDown - $now;
        $days = document.getElementById('days');
        $hours = document.getElementById('hours');
        $minutes = document.getElementById('minutes');
        $seconds = document.getElementById('seconds');
        $days.innerText = Math.floor($distance / $day);
        $hours.innerText = Math.floor($distance % $day / $hour);
        $minutes.innerText = Math.floor($distance % $hour / $minute);
        $seconds.innerText = Math.floor($distance % $minute / $second);

        if ($distance < 0) {
          clearInterval($x);
          console.log('END')
        }
      }), $second);
    }
  </script>

</body>
</html>
```
