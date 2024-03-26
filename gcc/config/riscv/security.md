;; RISC-V Custom Instructions for GCC
;; Assuming these are part of a custom extension or modification.
(define_c_enum "unspec" [
    ;; sec unspecs
    UNSPEC_SICT
    UNSPEC_SSRA
    UNSPEC_SSJA
])

;; Define sict instruction
(define_insn "riscv_sict_<mode>"
  [(set (match_operand:X 0 "register_operand" "+r")
        (unspec:X [(match_operand:X 1 "register_operand" "+r")
                    (match_operand:X 2 "register_operand" "+r")]
         UNSPEC_SICT))]
  "TARGET_XSEC"
  "sict\t%0, %1, %2"
  [(set_attr "type" "security")])

;; Define ssra instruction
(define_insn "riscv_ssra_<mode>"
  [(set (match_operand:X 0 "register_operand" "+r")
        (unspec:X [(match_operand:X 1 "register_operand" "+r")
                    (match_operand:X 2 "register_operand" "+r")]
         UNSPEC_SSRA))]
  "TARGET_XSEC"
  "ssra\t%0, %1, %2"
  [(set_attr "type" "security")])

;; Define ssja instruction
(define_insn "riscv_ssja_<mode>"
  [(set (match_operand:X 0 "register_operand" "+r")
        (unspec:X [(match_operand:X 1 "register_operand" "+r")
                    (match_operand:X 2 "register_operand" "+r")]
         UNSPEC_SSJA))]
  "TARGET_XSEC"
  "ssja\t%0, %1, %2"
  [(set_attr "type" "security")])
