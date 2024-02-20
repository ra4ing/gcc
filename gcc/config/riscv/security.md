;; RISC-V Custom Instructions for GCC
;; Assuming these are part of a custom extension or modification.
(define_c_enum "unspec" [
    ;; sec unspecs
    UNSPEC_SJALR
    UNSPEC_SICT
])


;; Define sjalr instruction
(define_insn "riscv_sjalr_<mode>"
  [(set (match_operand:X 0 "register_operand" "+r") ;; Destination register
        (unspec:X [(match_operand:X 1 "register_operand" "+r") ;; Source register 1
                    (match_operand:X 2 "register_operand" "+r")] ;; Source register 2
         UNSPEC_SJALR))]
  "TARGET_XOSEC"
  "sjalr\t%0, %1, %2"
  [(set_attr "type" "security")])

;; Define sict instruction
(define_insn "riscv_sict_<mode>"
  [(set (match_operand:X 0 "register_operand" "+r") ;; Destination register
        (unspec:X [(match_operand:X 1 "register_operand" "+r") ;; Source register 1
                    (match_operand:X 2 "register_operand" "+r")] ;; Source register 2
         UNSPEC_SICT))]
  "TARGET_XOSEC"
  "sict\t%0, %1, %2"
  [(set_attr "type" "security")])

