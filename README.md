django-admin startproject myproject
cd myproject
from django.db import models

class Product(models.Model):
    name = models.CharField(max_length=100)
    description = models.TextField()
    price = models.DecimalField(max_digits=10, decimal_places=2)

    def _str_(self):
        return self.name
from django.views.generic import ListView, DetailView, CreateView, UpdateView, DeleteView
from .models import Product
from django.urls import reverse_lazy

class ProductListView(ListView):
    model = Product

class ProductDetailView(DetailView):
    model = Product

class ProductCreateView(CreateView):
    model = Product
    fields = ['name', 'description', 'price']

class ProductUpdateView(UpdateView):
    model = Product
