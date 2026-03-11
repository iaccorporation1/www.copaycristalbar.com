import React, { useEffect } from "react";
import { motion } from "framer-motion";
import {
  Wine,
  GlassWater,
  Phone,
  MapPin,
  Clock,
  Star,
  Instagram,
  MessageCircle,
  PartyPopper,
} from "lucide-react";

const servicios = [
  {
    titulo: "Barra móvil para eventos",
    texto: "Llevamos una barra móvil profesional y elegante a eventos sociales, corporativos y celebraciones privadas en Chiclayo.",
    icono: PartyPopper,
  },
  {
    titulo: "Cocteles clásicos y de autor",
    texto: "Atendemos eventos con una propuesta de servicio ordenada, atractiva y adaptable al tipo de celebración.",
    icono: Wine,
  },
  {
    titulo: "Atención integral",
    texto: "Ofrecemos una atención cuidada, con presentación profesional y una barra móvil pensada para realzar tu evento.",
    icono: GlassWater,
  },
];

const paquetes = [
  {
    nombre: "Paquete Básico",
    detalle: "Ideal para reuniones, cumpleaños y encuentros especiales.",
    incluye: ["Barra móvil", "3 tipos de cocteles", "Bartender", "Insumos básicos"],
  },
  {
    nombre: "Paquete Premium",
    detalle: "Perfecto para celebraciones importantes y eventos corporativos.",
    incluye: ["Barra móvil equipada", "6 tipos de cocteles", "2 bartenders", "Cristalería y garnish"],
  },
  {
    nombre: "Paquete Personalizado",
    detalle: "Adaptado al tipo de evento, cantidad de asistentes y estilo de servicio requerido.",
    incluye: ["Carta a medida", "Presentación personalizada", "Opciones sin alcohol", "Asesoría previa"],
  },
];

const cocteles = [
  "Mojito",
  "Piña Colada",
  "Daiquiri",
  "Aperol Spritz",
  "Coctel tropical",
  "Opciones sin alcohol",
];

const galeria = [
  "/galeria/coctel1.jpg",
  "/galeria/coctel2.jpg",
  "/galeria/coctel3.jpg",
  "/galeria/coctel4.jpg",
  "/galeria/coctel5.jpg",
  "/galeria/coctel6.jpg",
  "/galeria/coctel7.jpg",
  "/galeria/coctel8.jpg",
];

const testimonios = [
  {
    nombre: "Clientes en Chiclayo",
    comentario: "Muy buena atención, excelente presentación y una barra móvil que dio una mejor imagen a nuestro evento.",
  },
  {
    nombre: "Evento corporativo",
    comentario: "Servicio puntual, ordenado y profesional. Muy recomendable para actividades institucionales y corporativas.",
  },
  {
    nombre: "Celebración familiar",
    comentario: "La atención fue muy buena y la presentación de la barra móvil hizo que la celebración se vea más elegante y organizada.",
  },
];

function Card({ className = "", children }) {
  return <div className={`rounded-[1.5rem] border border-white/10 ${className}`}>{children}</div>;
}

function CardContent({ className = "", children }) {
  return <div className={className}>{children}</div>;
}

function Button({ href, children, className = "", variant = "solid" }) {
  const base =
    "inline-flex items-center justify-center rounded-2xl px-6 py-4 text-base font-semibold transition duration-300";
  const styles =
    variant === "outline"
      ? "border border-white/20 bg-white/5 text-white hover:bg-white/10"
      : "bg-white text-neutral-950 hover:opacity-90";

  return (
    <a href={href} className={`${base} ${styles} ${className}`}>
      {children}
    </a>
  );
}

export default function PaginaWebCocteles() {
  useEffect(() => {
    document.title = "Copa & Cristal | Barra móvil para eventos en Chiclayo";

    const ensureMeta = (name, content) => {
      let meta = document.querySelector(`meta[name="${name}"]`);
      if (!meta) {
        meta = document.createElement("meta");
        meta.name = name;
        document.head.appendChild(meta);
      }
      meta.content = content;
    };

    const ensurePropertyMeta = (property, content) => {
      let meta = document.querySelector(`meta[property="${property}"]`);
      if (!meta) {
        meta = document.createElement("meta");
        meta.setAttribute("property", property);
        document.head.appendChild(meta);
      }
      meta.content = content;
    };

    const ensureLink = (rel, href) => {
      let link = document.querySelector(`link[rel="${rel}"]`);
      if (!link) {
        link = document.createElement("link");
        link.rel = rel;
        document.head.appendChild(link);
      }
      link.href = href;
    };

    ensureMeta(
      "description",
      "Barra móvil para eventos en Chiclayo | Copa & Cristal. Servicio profesional de cocteles, bartender y barra móvil para bodas, cumpleaños y eventos corporativos. Reservas por WhatsApp."
    );

    ensureMeta(
      "keywords",
      "barra móvil Chiclayo, bartender Chiclayo, cocteles para eventos Chiclayo, barra de tragos Chiclayo, servicio de coctelería Chiclayo, bodas Chiclayo, cumpleaños Chiclayo"
    );

    ensureLink("canonical", "https://copaycristalbar.com");
    ensurePropertyMeta("og:title", "Copa & Cristal | Barra móvil en Chiclayo");
    ensurePropertyMeta("og:description", "Servicio profesional de barra móvil y cocteles para eventos en Chiclayo.");
    ensurePropertyMeta("og:type", "website");
    ensurePropertyMeta("og:url", "https://copaycristalbar.com");

    const previousSchema = document.getElementById("schema-localbusiness");
    if (previousSchema) previousSchema.remove();

    const schema = {
      "@context": "https://schema.org",
      "@type": "LocalBusiness",
      "name": "Copa & Cristal",
      "image": "https://copaycristalbar.com/galeria/coctel1.jpg",
      "url": "https://copaycristalbar.com",
      "telephone": "+51940740477",
      "address": {
        "@type": "PostalAddress",
        "addressLocality": "Chiclayo",
        "addressCountry": "PE"
      },
      "description": "Barra móvil profesional para eventos en Chiclayo. Servicio de cocteles, bartender y barra de tragos para bodas, cumpleaños y eventos corporativos.",
      "areaServed": ["Chiclayo", "La Victoria", "José Leonardo Ortiz", "Pimentel", "Lambayeque"],
      "priceRange": "$$"
    };

    const script = document.createElement("script");
    script.id = "schema-localbusiness";
    script.type = "application/ld+json";
    script.text = JSON.stringify(schema);
    document.head.appendChild(script);

    return () => {
      const schemaNode = document.getElementById("schema-localbusiness");
      if (schemaNode) schemaNode.remove();
    };
  }, []);

  return (
    <div className="min-h-screen bg-[radial-gradient(circle_at_top,rgba(251,191,36,0.10),transparent_18%),linear-gradient(180deg,#09090b_0%,#111827_45%,#09090b_100%)] text-white">
      <header className="sticky top-0 z-40 border-b border-white/10 bg-black/40 backdrop-blur-xl">
        <div className="mx-auto flex max-w-7xl items-center justify-between px-6 py-4">
          <div className="absolute inset-x-0 top-0 -z-10 h-full bg-gradient-to-r from-amber-400/5 via-transparent to-pink-400/5" />
          <div>
            <h1 className="text-xl font-bold tracking-wide">COPA & CRISTAL</h1>
            <p className="text-xs text-white/60">Barra móvil y eventos en Chiclayo</p>
          </div>
          <nav className="hidden gap-6 text-sm font-medium text-white/80 md:flex">
            <a href="#servicios" className="hover:text-white">Servicios</a>
            <a href="#paquetes" className="hover:text-white">Paquetes</a>
            <a href="#cocteles" className="hover:text-white">Carta</a>
            <a href="#galeria" className="hover:text-white">Galería</a>
            <a href="#contacto" className="hover:text-white">Contacto</a>
          </nav>
        </div>
      </header>

      <section className="relative overflow-hidden border-b border-white/10">
        <div className="absolute inset-0 bg-[radial-gradient(circle_at_top_right,rgba(251,191,36,0.22),transparent_24%),radial-gradient(circle_at_left,rgba(236,72,153,0.20),transparent_24%),linear-gradient(180deg,rgba(255,255,255,0.02),transparent)]" />
        <div className="absolute inset-0 bg-[url('https://images.unsplash.com/photo-1514362545857-3bc16c4c7d1b?q=80&w=1600&auto=format&fit=crop')] bg-cover bg-center opacity-10" />
        <div className="mx-auto grid max-w-7xl items-center gap-10 px-6 py-20 md:grid-cols-2 md:py-28">
          <motion.div initial={{ opacity: 0, y: 20 }} animate={{ opacity: 1, y: 0 }} transition={{ duration: 0.6 }}>
            <span className="inline-flex rounded-full border border-amber-400/30 bg-amber-400/10 px-4 py-1 text-sm text-amber-300">
              Barra móvil y atención para eventos en Chiclayo
            </span>
            <h2 className="mt-5 text-5xl font-extrabold leading-tight tracking-tight md:text-7xl">
              Haz que tu evento se vea <span className="text-amber-300">más elegante</span> y memorable
            </h2>
            <p className="mt-5 max-w-xl text-lg leading-8 text-white/75">
              En <strong>Copa &amp; Cristal</strong> ofrecemos servicio de barra móvil para eventos en Chiclayo, con una presentación elegante, atención profesional y una experiencia ideal para celebraciones sociales y corporativas.
            </p>
            <div className="mt-8 flex flex-wrap gap-4">
              <div className="w-full text-sm text-white/60">Atención rápida • Presentación premium • Reservas por WhatsApp</div>
              <div className="w-full text-base font-medium text-amber-200">Barra móvil premium para bodas, cumpleaños y eventos corporativos en Chiclayo</div>
              <Button href="#contacto">Solicitar cotización</Button>
              <Button href="#paquetes" variant="outline">Ver paquetes</Button>
            </div>
            <div className="mt-8 flex flex-wrap gap-6 text-sm text-white/70">
              <div className="flex items-center gap-2"><Star className="h-4 w-4" /> Atención para eventos</div>
              <div className="flex items-center gap-2"><Star className="h-4 w-4" /> Barra móvil profesional</div>
              <div className="flex items-center gap-2"><Star className="h-4 w-4" /> Servicio en Chiclayo</div>
            </div>
          </motion.div>

          <motion.div initial={{ opacity: 0, scale: 0.96 }} animate={{ opacity: 1, scale: 1 }} transition={{ duration: 0.6, delay: 0.1 }}>
            <div className="rounded-[2rem] border border-white/10 bg-white/10 p-4 shadow-[0_20px_80px_rgba(0,0,0,0.45)] backdrop-blur-xl">
              <div className="grid gap-4 md:grid-cols-2">
                <div className="rounded-[1.5rem] bg-gradient-to-br from-amber-300/40 to-pink-400/25 p-6 shadow-lg">
                  <p className="text-sm text-white/70">Evento destacado</p>
                  <h3 className="mt-2 text-2xl font-bold">Copa & Cristal</h3>
                  <p className="mt-3 text-sm leading-7 text-white/75">
                    Llevamos una barra móvil elegante, funcional y bien presentada para realzar la imagen de tu evento.
                  </p>
                </div>
                <div className="rounded-[1.5rem] border border-white/10 bg-neutral-900/80 p-6">
                  <p className="text-sm text-white/70">Ideal para</p>
                  <ul className="mt-3 space-y-3 text-sm text-white/85">
                    <li>Bodas y aniversarios</li>
                    <li>Cumpleaños y reuniones</li>
                    <li>Eventos corporativos</li>
                    <li>Activaciones y ferias</li>
                  </ul>
                </div>
                <div className="rounded-[1.5rem] border border-white/10 bg-neutral-900/80 p-6 md:col-span-2">
                  <p className="text-sm text-white/70">Ventaja competitiva</p>
                  <p className="mt-3 text-lg font-semibold leading-8 text-white/90">
                    Brindamos una experiencia profesional de barra móvil que mejora la presentación, la atención y el ambiente de cada evento.
                  </p>
                </div>
              </div>
            </div>
          </motion.div>
        </div>
      </section>

      <section id="servicios" className="mx-auto max-w-7xl px-6 py-20">
        <div className="max-w-2xl">
          <p className="text-sm uppercase tracking-[0.2em] text-amber-300">Servicios</p>
          <h3 className="mt-3 text-3xl font-bold md:text-4xl">Todo lo que necesitas para una barra de cocteles profesional</h3>
        </div>
        <div className="mt-10 grid gap-6 md:grid-cols-3">
          {servicios.map((servicio, i) => {
            const Icono = servicio.icono;
            return (
              <motion.div
                key={servicio.titulo}
                initial={{ opacity: 0, y: 12 }}
                whileInView={{ opacity: 1, y: 0 }}
                viewport={{ once: true }}
                transition={{ duration: 0.4, delay: i * 0.1 }}
              >
                <Card className="h-full bg-white/5 shadow-xl transition duration-300 hover:-translate-y-2 hover:bg-white/10">
                  <CardContent className="p-6">
                    <div className="mb-4 inline-flex rounded-2xl bg-amber-300/15 p-3 text-amber-300">
                      <Icono className="h-6 w-6" />
                    </div>
                    <h4 className="text-xl font-semibold">{servicio.titulo}</h4>
                    <p className="mt-3 leading-7 text-white/70">{servicio.texto}</p>
                  </CardContent>
                </Card>
              </motion.div>
            );
          })}
        </div>
      </section>

      <section id="paquetes" className="bg-white/5 py-20 backdrop-blur-sm">
        <div className="mx-auto max-w-7xl px-6">
          <div className="max-w-2xl">
            <p className="text-sm uppercase tracking-[0.2em] text-amber-300">Paquetes</p>
            <h3 className="mt-3 text-3xl font-bold md:text-4xl">Servicio ideal para distintos tipos de eventos</h3>
          </div>
          <div className="mt-10 grid gap-6 md:grid-cols-3">
            {paquetes.map((paquete, i) => (
              <motion.div
                key={paquete.nombre}
                initial={{ opacity: 0, y: 12 }}
                whileInView={{ opacity: 1, y: 0 }}
                viewport={{ once: true }}
                transition={{ duration: 0.4, delay: i * 0.1 }}
              >
                <Card className="h-full bg-neutral-950/80 shadow-xl transition duration-300 hover:-translate-y-2 hover:border-amber-300/30">
                  <CardContent className="p-6">
                    <h4 className="text-2xl font-bold">{paquete.nombre}</h4>
                    <p className="mt-3 text-white/70">{paquete.detalle}</p>
                    <ul className="mt-5 space-y-3 text-sm text-white/85">
                      {paquete.incluye.map((item) => (
                        <li key={item} className="rounded-xl border border-white/10 bg-white/5 px-3 py-2">
                          {item}
                        </li>
                      ))}
                    </ul>
                  </CardContent>
                </Card>
              </motion.div>
            ))}
          </div>
        </div>
      </section>

      <section id="cocteles" className="mx-auto max-w-7xl px-6 py-20">
        <div className="grid gap-10 md:grid-cols-2 md:items-center">
          <div>
            <p className="text-sm uppercase tracking-[0.2em] text-amber-300">Carta de cocteles</p>
            <h3 className="mt-3 text-3xl font-bold md:text-4xl">Sabores que elevan la experiencia</h3>
            <p className="mt-4 max-w-xl leading-8 text-white/75">
              En Copa &amp; Cristal ofrecemos una atención profesional para eventos en Chiclayo, con barra móvil y una presentación que aporta elegancia y mejor experiencia para tus invitados.
            </p>
          </div>
          <div className="grid grid-cols-2 gap-4">
            {cocteles.map((item) => (
              <div key={item} className="rounded-[1.25rem] border border-white/10 bg-white/5 px-4 py-5 text-center text-sm font-medium text-white/90 shadow-lg transition duration-300 hover:scale-[1.03] hover:border-amber-300/30">
                {item}
              </div>
            ))}
          </div>
        </div>
      </section>

      <section id="galeria" className="mx-auto max-w-7xl px-6 py-20">
        <div className="max-w-2xl">
          <p className="text-sm uppercase tracking-[0.2em] text-amber-300">Galería</p>
          <h3 className="mt-3 text-3xl font-bold md:text-4xl">Nuestros cocteles y presentaciones</h3>
          <p className="mt-4 text-white/70">Algunas muestras de los cocteles y presentaciones que ofrecemos en nuestros eventos.</p>
        </div>

        <div className="mt-10 grid gap-6 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4">
          {galeria.map((img, i) => (
            <motion.div
              key={i}
              initial={{ opacity: 0, scale: 0.95 }}
              whileInView={{ opacity: 1, scale: 1 }}
              viewport={{ once: true }}
              transition={{ duration: 0.3, delay: i * 0.05 }}
              className="group overflow-hidden rounded-2xl border border-white/10 bg-white/5 shadow-lg"
            >
              <img
                src={img}
                alt={`Coctel Copa y Cristal ${i + 1}`}
                className="h-72 w-full object-cover transition duration-500 group-hover:scale-110 group-hover:brightness-110"
              />
            </motion.div>
          ))}
        </div>
      </section>

      <section className="mx-auto max-w-7xl px-6 py-20">
        <div className="grid gap-8 rounded-[2rem] border border-white/10 bg-white/5 p-8 shadow-xl md:grid-cols-2 md:p-10">
          <div>
            <p className="text-sm uppercase tracking-[0.2em] text-amber-300">Cobertura</p>
            <h3 className="mt-3 text-3xl font-bold md:text-4xl">Atendemos eventos en Chiclayo y alrededores</h3>
            <p className="mt-4 max-w-xl leading-8 text-white/75">
              Brindamos servicio de barra móvil en Chiclayo, La Victoria, José Leonardo Ortiz, Pimentel y Lambayeque, con atención puntual y presentación profesional.
            </p>
          </div>
          <div className="grid grid-cols-2 gap-4 text-sm text-white/85">
            {["Chiclayo", "La Victoria", "José Leonardo Ortiz", "Pimentel", "Lambayeque", "Eventos privados", "Eventos corporativos", "Reservas por WhatsApp"].map((zona) => (
              <div key={zona} className="rounded-2xl border border-white/10 bg-neutral-950/70 px-4 py-4 text-center">
                {zona}
              </div>
            ))}
          </div>
        </div>
      </section>

      <section className="bg-white/5 py-20">
        <div className="mx-auto max-w-7xl px-6">
          <div className="max-w-2xl">
            <p className="text-sm uppercase tracking-[0.2em] text-amber-300">Testimonios</p>
            <h3 className="mt-3 text-3xl font-bold md:text-4xl">Lo que opinan nuestros clientes</h3>
          </div>
          <div className="mt-10 grid gap-6 md:grid-cols-3">
            {testimonios.map((testimonio, i) => (
              <motion.div
                key={testimonio.nombre}
                initial={{ opacity: 0, y: 12 }}
                whileInView={{ opacity: 1, y: 0 }}
                viewport={{ once: true }}
                transition={{ duration: 0.4, delay: i * 0.1 }}
              >
                <Card className="h-full bg-neutral-950/80">
                  <CardContent className="p-6">
                    <div className="mb-4 flex gap-1 text-amber-300">
                      {Array.from({ length: 5 }).map((_, idx) => (
                        <Star key={idx} className="h-4 w-4 fill-current" />
                      ))}
                    </div>
                    <p className="leading-7 text-white/75">“{testimonio.comentario}”</p>
                    <p className="mt-5 font-semibold text-white/90">{testimonio.nombre}</p>
                  </CardContent>
                </Card>
              </motion.div>
            ))}
          </div>
        </div>
      </section>

      <section className="mx-auto max-w-7xl px-6 py-20">
        <div className="grid gap-8 md:grid-cols-2 md:items-center">
          <div>
            <p className="text-sm uppercase tracking-[0.2em] text-amber-300">Ubicación</p>
            <h3 className="mt-3 text-3xl font-bold md:text-4xl">Encuéntranos y reserva tu fecha</h3>
            <p className="mt-4 max-w-xl leading-8 text-white/75">
              Estamos listos para atender eventos en Chiclayo y zonas cercanas. Escríbenos por WhatsApp para cotizar y coordinar disponibilidad.
            </p>
          </div>
          <div className="overflow-hidden rounded-[2rem] border border-white/10 bg-white/5 shadow-xl">
            <iframe
              title="Mapa Copa y Cristal Chiclayo"
              src="https://www.google.com/maps?q=Chiclayo%20Peru&z=12&output=embed"
              width="100%"
              height="360"
              loading="lazy"
              referrerPolicy="no-referrer-when-downgrade"
              className="min-h-[360px] w-full"
            />
          </div>
        </div>
      </section>

      <section id="contacto" className="mx-auto max-w-7xl px-6 py-20">
        <div className="grid gap-8 rounded-[2rem] border border-white/10 bg-gradient-to-r from-amber-400/15 to-pink-400/15 p-8 shadow-[0_20px_80px_rgba(0,0,0,0.4)] md:grid-cols-2 md:p-10">
          <div>
            <p className="text-sm uppercase tracking-[0.2em] text-amber-300">Contacto</p>
            <h3 className="mt-3 text-3xl font-bold md:text-4xl">Solicita tu cotización hoy</h3>
            <p className="mt-4 max-w-xl leading-8 text-white/75">
              En Copa &amp; Cristal ofrecemos una atención profesional para eventos en Chiclayo, con barra móvil y una presentación que aporta elegancia y mejor experiencia para tus invitados.
            </p>
          </div>
          <div className="space-y-4 rounded-[1.5rem] border border-white/10 bg-neutral-950/70 p-6">
            <div className="flex items-center gap-3 text-white/85"><Phone className="h-5 w-5 text-amber-300" /> +51 940 740 477</div>
            <div className="flex items-center gap-3 text-white/85"><Instagram className="h-5 w-5 text-amber-300" /> Chiclayo, 14001</div>
            <div className="flex items-center gap-3 text-white/85"><MapPin className="h-5 w-5 text-amber-300" /> Atención en Chiclayo y zonas cercanas</div>
            <div className="flex items-center gap-3 text-white/85"><Clock className="h-5 w-5 text-amber-300" /> Reservas sujetas a disponibilidad</div>
            <div className="pt-3">
              <Button href="https://wa.me/51940740477" className="flex w-full gap-2 bg-white text-neutral-950 hover:opacity-90">
                <MessageCircle className="h-5 w-5" /> Escribir por WhatsApp
              </Button>
            </div>
          </div>
        </div>
      </section>

      <footer className="border-t border-white/10 px-6 py-8 text-center text-sm text-white/50">
        © 2026 Copa & Cristal. Todos los derechos reservados.
      </footer>

      <a
        href="https://wa.me/51940740477?text=Hola%2C%20quiero%20informaci%C3%B3n%20sobre%20barra%20m%C3%B3vil%20para%20eventos"
        target="_blank"
        rel="noreferrer"
        className="fixed bottom-6 right-6 z-50 flex items-center gap-3 rounded-full bg-green-500 px-5 py-3 font-semibold text-white shadow-[0_10px_30px_rgba(34,197,94,0.4)] transition duration-300 hover:scale-105 hover:bg-green-600"
      >
        <MessageCircle className="h-5 w-5" /> WhatsApp
      </a>
    </div>
  );
}
