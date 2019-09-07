; Bitcrush Upscaler - Use legacy VERSION 3 syntax.
(setq sourcerate 4000) ; Source samplerate
(setq multiplier (/ 44100 sourcerate)) ; New samplerate


(defun bad-resample (sig num)
  (setq size 1000)
  (setf s-array (make-array (* num size)))
  (setf end-array
    (if (/= (rem (truncate len) size) 0)
      (make-array (* num (rem (truncate len) size)))
      nil))
  (setf output (s-rest 0))
  (dotimes (count (truncate (/ len size)))
    (fill-array s-array sig num)
    (setf output
      (sim
        output
        (at-abs (/ (* count num size) *sound-srate*)
          (cue (snd-from-array 0 *sound-srate* s-array))))))
  (if end-array
    (progn
      (fill-array end-array sig num)
      (sim
        output
        (at-abs (/ (* (truncate (/ len size)) (* num size)) *sound-srate*)
          (cue (snd-from-array 0 *sound-srate* end-array)))))
    output))

(defun fill-array (s-a sig times)
  (dotimes (count (/ (length s-a) times))
    (let ((next (snd-fetch sig)))
      (dotimes (i times)
        (setf (aref s-a (+ i (* count times))) next)))))

(multichan-expand #'bad-resample s (truncate multiplier))