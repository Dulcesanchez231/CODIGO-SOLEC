# CODIGO-SOLEC
ACTIVIDAD 3
create service appointments(
    id INT AUTO_INCREMENT PRIMARY KEY,
    cliente VARCHAR(100),
    fecha DATE, 
    hora TIME,   
    servicio VARCHAR(255), 
);
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;
import java.util.List;

@Service
public class CitasService {

    @Autowired
    private CitasRepository citasRepository;

    public List<Cita> obtenerTodasLasCitas() {
        return citasRepository.findAll();
    }

    public void agregarCita(Cita cita) {
        citasRepository.save(cita);
    }
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;
import java.util.List;

@Service
public class CitasService {

    @Autowired
    private CitasRepository citasRepository;

    public List<Cita> obtenerTodasLasCitas() {
        return citasRepository.findAll();
    }

    public void agregarCita(Cita cita) {
        citasRepository.save(cita);
    }
}
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;

import java.util.List;

@RestController
@RequestMapping("/citas")
public class CitasController {

    @Autowired
    private CitasService citasService;

    @GetMapping
    public List<Cita> obtenerTodasLasCitas() {
        return citasService.obtenerTodasLasCitas();
    }

    @PostMapping
    public void agregarCita(@RequestBody Cita cita) {
        citasService.agregarCita(cita);
    }
}
import javax.persistence.Entity;
import javax.persistence.GeneratedValue;
import javax.persistence.GenerationType;
import javax.persistence.Id;
import java.util.Date;

@Entity
public class Cita {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String cliente;
    private Date fecha;
    private String hora;
    private String servicio;

    // Getters y Setters
}
