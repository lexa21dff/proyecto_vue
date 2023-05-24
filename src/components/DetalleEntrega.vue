<template>
    <div>
      <div class="container">
        <b-card class="m-1 p-3">
          <div v-if="entrega">
            <div class="row">
              <div class="col-lg-1 col-md-1">
                <img class="imagen" src="../assets/2.jpg" alt="">
              </div>
              <div class="col-lg-9">
                <h3>{{ entrega.proyecto.nombre }}</h3>
                <p><span class="fw-lighter">Calificación: </span>{{ entrega.calificacion }}</p>
              </div>
            </div>
            <div class="row">
              <p class="fw-lighter">Descripción de la entrega:</p>
              <p>{{ entrega.descripcion_entrega }}</p>
            </div>
            <div class="row">
              <p class="fw-lighter">Respuesta del instructor:</p>
              <p>{{ entrega.respuesta_instructor }}</p>
            </div>
            <div class="row">
              <p class="fw-lighter">Instructor:</p>
              <p>{{ entrega.instructor }}</p>
            </div>
            <div class="row">
              <p class="fw-lighter">Autor:</p>
              <p>{{ entrega.autor }}</p>
            </div>
            <div class="row">
              <p class="fw-lighter">Creado:</p>
              <p>{{ entrega.creado }}</p>
            </div>
            <div class="row">
              <p class="fw-lighter">Editado:</p>
              <p>{{ entrega.editado }}</p>
            </div>
          </div>
          <div v-else>
            <p>Loading...</p>
          </div>
        </b-card>
      </div>
    </div>
  </template>
  