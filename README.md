# codingame

## Les températures proche de zéro

```php
<?php

function computeClosestToZero(array $ts) {

  if (empty($ts) || in_array(0, $ts)) {
    return 0;
  }

  $neg = array_filter($ts, function($val) {
    return $val < 0;
  });

  $pos = array_diff($ts, $neg);

  $maxNeg = max($neg);
  $minPos = min($pos);

  if (abs($maxNeg) < $minPos) {
    return $maxNeg;
  }
  
  return $minPos;
}

/* Ignore and do not change the code below */
//region
fscanf(STDIN, "%d", $n);
$ts = array();
$inputs = explode(" ", fgets(STDIN));
for ($i = 0; $i < $n; $i++) {
    $ts[$i] = intval($inputs[$i]);
}
$oldStdout = fopen('php://stdout', 'wb');
eio_dup2(STDERR, STDOUT);
eio_event_loop();
$solution = computeClosestToZero($ts);
eio_dup2($oldStdout, STDOUT);
eio_event_loop();
echo "$solution
";
//endregion
?>
```

## Boîte la plus lourde

```php
<?php

function solve($weight0, $weight1, $weight2) {
  // Write your code here
  // To debug (equivalent to var_dump): error_log(var_export($var, true));

  $weights = [0 => $weight0, 1 => $weight1, 2 => $weight2];
  $heaviest = max($weights);

  $key = array_search($heaviest, $weights);

  return $key;
}

/* Ignore and do not change the code below */
//region

// game loop
while (TRUE)
{
    fscanf(STDIN, "%d", $weight0);
    fscanf(STDIN, "%d", $weight1);
    fscanf(STDIN, "%d", $weight2);
    $oldStdout = fopen('php://stdout', 'wb');
    eio_dup2(STDERR, STDOUT);
    eio_event_loop();
    $action = solve($weight0, $weight1, $weight2);
    eio_dup2($oldStdout, STDOUT);
    eio_event_loop();
    echo "$action
";
}
//endregion
?>
```
