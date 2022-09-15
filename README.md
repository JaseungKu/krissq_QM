# General rules for design 
- Design for interface.
- Make it most insensitive to human-error
- Keep scalability in mind
- Make it modular
- Make it easy for scripting
- Make it easy to extend
- Obey SOLID principle as much as possible
    - Single responsibility principle
    - Open-closed principle: open for  extension, close for modification
    - Liskov substitution principle
    - Interface segregation principle
    - Dependency inversion principle
 - Obey PEP8
 - Make a good documentation
 
# krissq_QM: kriss quantum Quantum Machine package

Conventions for setting up config

  - For qubit elements, use q0, q1, q2, ...
  - For resonator elements, use r0, r1, r2, ...
  - For CR elements, use cr01, where 0 is the index of control qubit, and 1 is the index of target qubit.

How qm configuration is generated:
 - `qm_config_params.json` is used to build `qm_config` dictionary, which is passed to the `open_qm` function. One needs to modify `qm_config_params.json` only. 
 - `qm_config_params.json` file is stored in the designated `config` folder, which is defined in `configuration.py`.

File handling
  - `FileHandler` class takes care of saving experimental parameters, qm_config_params, qm_config, data, and figure.
  - The class is currently defined in `configuration.py`.
  
Modules:`
- configuration : FileHandler, build_qm_config(), ...
- instrument: Collection of instrument drivers
- plotter
- utility:load_data, plotting, ...
- analysis
    - Fitting functions with some standard interface
        - Resonator fit, qubit_spec
        - Rabi amp fit for rough piamp and pi2amp
        - T1 fit, Ramsey fit
        - QST, QPT, RB ... fits
        - HamiltonianTomoFit
 - library: library of experiments for calibration, characterization and verification. Sort of list of standard toolkit, something that can be used routinely.
    - Calibration
        - RamseyCal
        - RabiAmpCal
        - DragCal
        - Pi2Cal
        - PiCal
        - CRAmpCal
        - CRPhaseCal
        - CRLengthCal
        - siZZle
        - CR tomo to cancel classical crosstalk
        - direct CR cal?

    - Characterization
        - Resonator/qubit Spectroscopy
        - Rabi, T1, Ramsey, Echo
        - Readout assignment fidelity
        - Find optimal readout length
        - Find optimal kernel (matched filter)
        - QP parity
        - Effective temperature meas
        - JAZZ
        
    - Verification: tomography, benchmarking, ... for measuring gate fidelity, quantum circuit fidelity, and etc.
        - QST
        - QPT
        - GST
        - RB
        - Leakage RB
        - Purity RB
        - Cycle benchmarking (CB)
        - Cross entropy benchmarking (XEB)    
        - QV (Quantum Volume)

