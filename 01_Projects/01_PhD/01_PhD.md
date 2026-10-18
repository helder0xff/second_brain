# Description
PhD, en el que estudiaré cómo afectaría el uso de un IMU basado en eventos en una aplicación como el VIO.

# ONGOING
- Chamorro's VIO.

# TODO
1. [[Filtered based methods]]
2. WP3: Neuromorphic (evt based) kalman filter
	1. Wang, Z., Ng, Y., Scheerlinck, C., & Mahony, R. (2021). An  asynchronous kalman filter for hybrid event cameras. In 2021 IEEE/CVF International Conference on Computer Vision (ICCV), (pp. 438–447). https://doi.org/10.1109/ICCV48922.2021.00050
# DONE
- 2026-09-15 Roadmap 2026-09-15
- 2026-09-15 [[Survery Paper]] 2026-10-10 
# Issues
- Did not present the anual report on the progress on time.
# Questions?
## Main Questions
1. Which researchs use event based data directly into their algorithms and how do they use them? (specially those coming from event base cameras)
2. In those researchs how the IMU data is used? (looking for a way to input event based IMU data)
3. Could path integration algorithm be used for end to end neuromorphic VIO?
## Side Questions
- How to correct event based cameras scale factor.
- Benefits and drawbacks of each event-based data representation.
- How does the racing drones work? 
	- Do they optimize its pass through the squares? 
	- Can we use physical AI for that? (As a previous step for humanoid motion?)
	- Here comes de NIMU
# Ideas
- When mixing frame based and event based cameras for feature based methods (feature extraction), for the sake of computational resources, when the event based robust features decay, use frame based use to top up features.
- **Acuity (foveation)**: use event-based camera for ROI detection (an object on x,y), and then point the frame-based camera to the centre of that point.
- For **motion models based methods**, a **model update** depending on the circunstances might help.

# Roadmap
![[Pasted image 20260918135911.png]]
# Links
- [[01_nSLAM]]
- [Correo UPM](https://www.upm.es/webmail_alumnos/?_task=mail&_mbox=INBOX)
- [Polictécnica Virtual][https://www.upm.es/politecnica_virtual/principal.upm?UPMSSID=dfa258898f465f672ccbf41cbefd881a]
- [Sede electrónica][https://sede.upm.es/TiProceeding/ciudadano?idLogica=misConvocatorias&entrada=ciudadano&idEntidad=UPM&fkIdioma=es]
# Resources
- https://onlinelibrary.wiley.com/doi/book/10.1002/9781118927601





