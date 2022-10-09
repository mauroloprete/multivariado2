# Laboratorio con Tidymodels



## Laboratorio de Splines


### B-Splines

#### Creando el modelo {-}


```r

# Defino el tipo de modelo

parsnip::linear_reg() %>%
    parsnip::set_engine("lm") %>%
    parsnip::set_mode('regression') %>%
    assign(
        "lm_mod",
        .,
        envir = .GlobalEnv
    )

# Receta : usando step_bs 

recipes::recipe(
    wage ~ age,
    data = Wage
) %>%
    recipes::step_bs(
        age,
        options = list(
          knots = c(25,50,60)
        )
    ) %>%
    recipes::prep() %>%
    assign(
        "recipe_bs",
        .,
        envir = .GlobalEnv
    )

# Usando la receta (Si lo hago de esta manera me da diferente al libro!)

workflows::workflow() %>%
    workflows::add_model(lm_mod) %>%
    workflows::add_recipe(recipe_bs) %>%
    generics::fit(
        data = Wage
    ) %>%
    assign(
        "model_wkf",
        .,
        envir = .GlobalEnv
    )

tidy.gt_table(model_wkf)
```

```{=html}
<div id="svjglnrcqb" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>@import url("https://fonts.googleapis.com/css2?family=Lato:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Lato, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#svjglnrcqb .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: #FFFFFF;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#svjglnrcqb .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#svjglnrcqb .gt_title {
  color: #333333;
  font-size: 24px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#svjglnrcqb .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 0;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#svjglnrcqb .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#svjglnrcqb .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#svjglnrcqb .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#svjglnrcqb .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#svjglnrcqb .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#svjglnrcqb .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#svjglnrcqb .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#svjglnrcqb .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#svjglnrcqb .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#svjglnrcqb .gt_from_md > :first-child {
  margin-top: 0;
}

#svjglnrcqb .gt_from_md > :last-child {
  margin-bottom: 0;
}

#svjglnrcqb .gt_row {
  padding-top: 7px;
  padding-bottom: 7px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #F6F7F7;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#svjglnrcqb .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
}

#svjglnrcqb .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}

#svjglnrcqb .gt_row_group_first td {
  border-top-width: 2px;
}

#svjglnrcqb .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#svjglnrcqb .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}

#svjglnrcqb .gt_first_summary_row.thick {
  border-top-width: 2px;
}

#svjglnrcqb .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#svjglnrcqb .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#svjglnrcqb .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#svjglnrcqb .gt_striped {
  background-color: #FAFAFA;
}

#svjglnrcqb .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#svjglnrcqb .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#svjglnrcqb .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-left: 4px;
  padding-right: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#svjglnrcqb .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#svjglnrcqb .gt_sourcenote {
  font-size: 12px;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#svjglnrcqb .gt_left {
  text-align: left;
}

#svjglnrcqb .gt_center {
  text-align: center;
}

#svjglnrcqb .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#svjglnrcqb .gt_font_normal {
  font-weight: normal;
}

#svjglnrcqb .gt_font_bold {
  font-weight: bold;
}

#svjglnrcqb .gt_font_italic {
  font-style: italic;
}

#svjglnrcqb .gt_super {
  font-size: 65%;
}

#svjglnrcqb .gt_footnote_marks {
  font-style: italic;
  font-weight: normal;
  font-size: 75%;
  vertical-align: 0.4em;
}

#svjglnrcqb .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}

#svjglnrcqb .gt_indent_1 {
  text-indent: 5px;
}

#svjglnrcqb .gt_indent_2 {
  text-indent: 10px;
}

#svjglnrcqb .gt_indent_3 {
  text-indent: 15px;
}

#svjglnrcqb .gt_indent_4 {
  text-indent: 20px;
}

#svjglnrcqb .gt_indent_5 {
  text-indent: 25px;
}
</style>
<table class="gt_table">
  
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col">Coeficiente</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" scope="col">Estimación</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" scope="col">Error estandar</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" scope="col">Estadístico</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" scope="col">P-valor</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr><td class="gt_row gt_left">(Intercept)</td>
<td class="gt_row gt_right">58.69</td>
<td class="gt_row gt_right">4.01</td>
<td class="gt_row gt_right">14.63</td>
<td class="gt_row gt_right">0.00</td></tr>
    <tr><td class="gt_row gt_left gt_striped">age_bs_1</td>
<td class="gt_row gt_right gt_striped">102.64</td>
<td class="gt_row gt_right gt_striped">11.45</td>
<td class="gt_row gt_right gt_striped">8.96</td>
<td class="gt_row gt_right gt_striped">0.00</td></tr>
    <tr><td class="gt_row gt_left">age_bs_2</td>
<td class="gt_row gt_right">48.76</td>
<td class="gt_row gt_right">8.62</td>
<td class="gt_row gt_right">5.65</td>
<td class="gt_row gt_right">0.00</td></tr>
    <tr><td class="gt_row gt_left gt_striped">age_bs_3</td>
<td class="gt_row gt_right gt_striped">40.80</td>
<td class="gt_row gt_right gt_striped">12.11</td>
<td class="gt_row gt_right gt_striped">3.37</td>
<td class="gt_row gt_right gt_striped">0.00</td></tr>
  </tbody>
  
  
</table>
</div>
```

Si no uso la receta y uso la formula adentro del fit me da igual que el libro. Descubrí que existe un bug al usar **step_bs()** e indicar la cantidad de nodos, lo publiqué en el foro de eva.



```r

lm_mod %>%
  generics::fit(
    wage ~ splines::bs(
        age,
        knots = c(
            25,
            40,
            60
        )
    ),
    data = Wage
  ) %>% 
  assign(
    "model",
    .,
    envir = .GlobalEnv
  )



tidy.gt_table(model)
```

```{=html}
<div id="zetiogdgrx" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>@import url("https://fonts.googleapis.com/css2?family=Lato:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Lato, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#zetiogdgrx .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: #FFFFFF;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#zetiogdgrx .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#zetiogdgrx .gt_title {
  color: #333333;
  font-size: 24px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#zetiogdgrx .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 0;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#zetiogdgrx .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#zetiogdgrx .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#zetiogdgrx .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#zetiogdgrx .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#zetiogdgrx .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#zetiogdgrx .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#zetiogdgrx .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#zetiogdgrx .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#zetiogdgrx .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#zetiogdgrx .gt_from_md > :first-child {
  margin-top: 0;
}

#zetiogdgrx .gt_from_md > :last-child {
  margin-bottom: 0;
}

#zetiogdgrx .gt_row {
  padding-top: 7px;
  padding-bottom: 7px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #F6F7F7;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#zetiogdgrx .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
}

#zetiogdgrx .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}

#zetiogdgrx .gt_row_group_first td {
  border-top-width: 2px;
}

#zetiogdgrx .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#zetiogdgrx .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}

#zetiogdgrx .gt_first_summary_row.thick {
  border-top-width: 2px;
}

#zetiogdgrx .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#zetiogdgrx .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#zetiogdgrx .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#zetiogdgrx .gt_striped {
  background-color: #FAFAFA;
}

#zetiogdgrx .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#zetiogdgrx .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#zetiogdgrx .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-left: 4px;
  padding-right: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#zetiogdgrx .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#zetiogdgrx .gt_sourcenote {
  font-size: 12px;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#zetiogdgrx .gt_left {
  text-align: left;
}

#zetiogdgrx .gt_center {
  text-align: center;
}

#zetiogdgrx .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#zetiogdgrx .gt_font_normal {
  font-weight: normal;
}

#zetiogdgrx .gt_font_bold {
  font-weight: bold;
}

#zetiogdgrx .gt_font_italic {
  font-style: italic;
}

#zetiogdgrx .gt_super {
  font-size: 65%;
}

#zetiogdgrx .gt_footnote_marks {
  font-style: italic;
  font-weight: normal;
  font-size: 75%;
  vertical-align: 0.4em;
}

#zetiogdgrx .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}

#zetiogdgrx .gt_indent_1 {
  text-indent: 5px;
}

#zetiogdgrx .gt_indent_2 {
  text-indent: 10px;
}

#zetiogdgrx .gt_indent_3 {
  text-indent: 15px;
}

#zetiogdgrx .gt_indent_4 {
  text-indent: 20px;
}

#zetiogdgrx .gt_indent_5 {
  text-indent: 25px;
}
</style>
<table class="gt_table">
  
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col">Coeficiente</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" scope="col">Estimación</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" scope="col">Error estandar</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" scope="col">Estadístico</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" scope="col">P-valor</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr><td class="gt_row gt_left">(Intercept)</td>
<td class="gt_row gt_right">60.49</td>
<td class="gt_row gt_right">9.46</td>
<td class="gt_row gt_right">6.39</td>
<td class="gt_row gt_right">0.00</td></tr>
    <tr><td class="gt_row gt_left gt_striped">splines::bs(age, knots = c(25, 40, 60))1</td>
<td class="gt_row gt_right gt_striped">3.98</td>
<td class="gt_row gt_right gt_striped">12.54</td>
<td class="gt_row gt_right gt_striped">0.32</td>
<td class="gt_row gt_right gt_striped">0.75</td></tr>
    <tr><td class="gt_row gt_left">splines::bs(age, knots = c(25, 40, 60))2</td>
<td class="gt_row gt_right">44.63</td>
<td class="gt_row gt_right">9.63</td>
<td class="gt_row gt_right">4.64</td>
<td class="gt_row gt_right">0.00</td></tr>
    <tr><td class="gt_row gt_left gt_striped">splines::bs(age, knots = c(25, 40, 60))3</td>
<td class="gt_row gt_right gt_striped">62.84</td>
<td class="gt_row gt_right gt_striped">10.76</td>
<td class="gt_row gt_right gt_striped">5.84</td>
<td class="gt_row gt_right gt_striped">0.00</td></tr>
    <tr><td class="gt_row gt_left">splines::bs(age, knots = c(25, 40, 60))4</td>
<td class="gt_row gt_right">55.99</td>
<td class="gt_row gt_right">10.71</td>
<td class="gt_row gt_right">5.23</td>
<td class="gt_row gt_right">0.00</td></tr>
    <tr><td class="gt_row gt_left gt_striped">splines::bs(age, knots = c(25, 40, 60))5</td>
<td class="gt_row gt_right gt_striped">50.69</td>
<td class="gt_row gt_right gt_striped">14.40</td>
<td class="gt_row gt_right gt_striped">3.52</td>
<td class="gt_row gt_right gt_striped">0.00</td></tr>
    <tr><td class="gt_row gt_left">splines::bs(age, knots = c(25, 40, 60))6</td>
<td class="gt_row gt_right">16.61</td>
<td class="gt_row gt_right">19.13</td>
<td class="gt_row gt_right">0.87</td>
<td class="gt_row gt_right">0.39</td></tr>
  </tbody>
  
  
</table>
</div>
```

#### Predición {-}



```r

age.grid <- seq(
    from = min(Wage$age), 
    to = max(Wage$age)
)

predict <- predict_df(
  model,
  tibble::tibble(age = age.grid)
)

Wage %>%
  ggplot(
    aes(
      x = age,
      y = wage
    )
  ) + 
  geom_point(
    alpha = 0.7,
    color = "gray"
  ) + 
  geom_line(
    aes(
      x = age,
      y = .pred
    ),
    data = predict,
    linetype = "dashed",
    size = 1.4
  ) + 
  geom_ribbon(
    aes(
      x = age,
      ymin = .pred_lower,
      ymax = .pred_upper,
      y = NULL
    ),
    data = predict,
    color = NA, 
    alpha = 0.4
  ) + 
  geom_vline(
    xintercept = c(
      25,
      40,
      60
    ),
    size = 1.4,
    colour = "blue",
    linetype = "dashed"
  ) + 
  labs(
    x = "Edad",
    y = "Salario",
    title = bquote("B-Splines con nodos en 25,40,60")
  ) + 
  theme_bw()
```

<img src="4-tidymodels_files/figure-html/unnamed-chunk-4-1.png" width="672" />

### Splines naturales 


```r

recipes::recipe(
    wage ~ age,
    data = Wage
) %>%
    recipes::step_ns(
        age,
        deg_free = 4
    ) %>%
    recipes::prep() %>%
    assign(
        "recipe_ns",
        .,
        envir = .GlobalEnv
    )


workflows::workflow() %>%
    workflows::add_model(lm_mod) %>%
    workflows::add_recipe(recipe_ns) %>%
    generics::fit(
        data = Wage
    ) %>%
    assign(
        "model_wkf.ns",
        .,
        envir = .GlobalEnv
    )

predict_ns <- predict_df(
  model_wkf.ns,
  tibble::tibble(age = age.grid)
)


Wage %>%
  ggplot(
    aes(
      x = age,
      y = wage
    )
  ) + 
  geom_point(
    alpha = 0.7,
    color = "gray"
  ) + 
  geom_line(
    aes(
      x = age,
      y = .pred
    ),
    data = predict_ns,
    linetype = "dashed",
    size = 1.4,
    color = "#E001B4"
  ) + 
  geom_ribbon(
    aes(
      x = age,
      ymin = .pred_lower,
      ymax = .pred_upper,
      y = NULL
    ),
    data = predict_ns,
    color = "#E001B4", 
    alpha = 0.4
  ) + 
  ggformula::geom_spline(
    df = 16,
    size = 1.2,
    colour = "#0247FF"
  ) + 
  ggformula::geom_spline(
    cv = TRUE,
    colour = "red",
    size = 1.2
  ) + 
  labs(
    x = "Edad",
    y = "Salario",
    title = "**Splines naturales y ajuste por spline**",
    subtitle = "**Natural spline con** <span style='color:#E001B4;'>df = 4</span>, <span                           style='color:#0247FF;'>df = 16</span> y <span style= 'color:#FF0202;'>df por CV</span>"
  ) + 
  theme(
    text = element_text(
      family = "Meera",
      size = 16
    ),
    plot.title = element_markdown(size = 16),
    plot.subtitle = element_markdown(size = 16)
  )
```

<img src="4-tidymodels_files/figure-html/unnamed-chunk-5-1.png" width="672" />

### Método lowess (Regresión local)




## Laboratorio GAMs

### Utilizando MCO


```r


recipes::recipe(
  wage ~ year + age + education,
  data = Wage
) %>%
recipes::step_ns(
  year,
  deg_free = 4
) %>%
recipes::step_ns(
  age,
  deg_free = 5
) %>%
assign(
  "recipe_gams",
  .,
  envir = .GlobalEnv
)



workflows::workflow() %>%
    workflows::add_model(lm_mod) %>%
    workflows::add_recipe(recipe_gams) %>%
    generics::fit(
        data = Wage
    ) %>%
    assign(
        "model_wkf.gamsMCO",
        .,
        envir = .GlobalEnv
    )

tidy.gt_table(
  model_wkf.gamsMCO
)
```

```{=html}
<div id="lowkdyhtls" style="overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>@import url("https://fonts.googleapis.com/css2?family=Lato:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");
html {
  font-family: Lato, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#lowkdyhtls .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 3px;
  border-top-color: #FFFFFF;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#lowkdyhtls .gt_heading {
  background-color: #FFFFFF;
  text-align: left;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#lowkdyhtls .gt_title {
  color: #333333;
  font-size: 24px;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#lowkdyhtls .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 0;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#lowkdyhtls .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#lowkdyhtls .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#lowkdyhtls .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#lowkdyhtls .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#lowkdyhtls .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#lowkdyhtls .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#lowkdyhtls .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#lowkdyhtls .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
}

#lowkdyhtls .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#lowkdyhtls .gt_from_md > :first-child {
  margin-top: 0;
}

#lowkdyhtls .gt_from_md > :last-child {
  margin-bottom: 0;
}

#lowkdyhtls .gt_row {
  padding-top: 7px;
  padding-bottom: 7px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #F6F7F7;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#lowkdyhtls .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 80%;
  font-weight: bolder;
  text-transform: uppercase;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
}

#lowkdyhtls .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}

#lowkdyhtls .gt_row_group_first td {
  border-top-width: 2px;
}

#lowkdyhtls .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#lowkdyhtls .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}

#lowkdyhtls .gt_first_summary_row.thick {
  border-top-width: 2px;
}

#lowkdyhtls .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#lowkdyhtls .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#lowkdyhtls .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#lowkdyhtls .gt_striped {
  background-color: #FAFAFA;
}

#lowkdyhtls .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#lowkdyhtls .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#lowkdyhtls .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-left: 4px;
  padding-right: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#lowkdyhtls .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#lowkdyhtls .gt_sourcenote {
  font-size: 12px;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#lowkdyhtls .gt_left {
  text-align: left;
}

#lowkdyhtls .gt_center {
  text-align: center;
}

#lowkdyhtls .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#lowkdyhtls .gt_font_normal {
  font-weight: normal;
}

#lowkdyhtls .gt_font_bold {
  font-weight: bold;
}

#lowkdyhtls .gt_font_italic {
  font-style: italic;
}

#lowkdyhtls .gt_super {
  font-size: 65%;
}

#lowkdyhtls .gt_footnote_marks {
  font-style: italic;
  font-weight: normal;
  font-size: 75%;
  vertical-align: 0.4em;
}

#lowkdyhtls .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}

#lowkdyhtls .gt_indent_1 {
  text-indent: 5px;
}

#lowkdyhtls .gt_indent_2 {
  text-indent: 10px;
}

#lowkdyhtls .gt_indent_3 {
  text-indent: 15px;
}

#lowkdyhtls .gt_indent_4 {
  text-indent: 20px;
}

#lowkdyhtls .gt_indent_5 {
  text-indent: 25px;
}
</style>
<table class="gt_table">
  
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col">Coeficiente</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" scope="col">Estimación</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" scope="col">Error estandar</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" scope="col">Estadístico</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" scope="col">P-valor</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr><td class="gt_row gt_left">(Intercept)</td>
<td class="gt_row gt_right">46.95</td>
<td class="gt_row gt_right">4.70</td>
<td class="gt_row gt_right">9.98</td>
<td class="gt_row gt_right">0.00</td></tr>
    <tr><td class="gt_row gt_left gt_striped">education2. HS Grad</td>
<td class="gt_row gt_right gt_striped">10.98</td>
<td class="gt_row gt_right gt_striped">2.43</td>
<td class="gt_row gt_right gt_striped">4.52</td>
<td class="gt_row gt_right gt_striped">0.00</td></tr>
    <tr><td class="gt_row gt_left">education3. Some College</td>
<td class="gt_row gt_right">23.47</td>
<td class="gt_row gt_right">2.56</td>
<td class="gt_row gt_right">9.16</td>
<td class="gt_row gt_right">0.00</td></tr>
    <tr><td class="gt_row gt_left gt_striped">education4. College Grad</td>
<td class="gt_row gt_right gt_striped">38.31</td>
<td class="gt_row gt_right gt_striped">2.55</td>
<td class="gt_row gt_right gt_striped">15.04</td>
<td class="gt_row gt_right gt_striped">0.00</td></tr>
    <tr><td class="gt_row gt_left">education5. Advanced Degree</td>
<td class="gt_row gt_right">62.55</td>
<td class="gt_row gt_right">2.76</td>
<td class="gt_row gt_right">22.65</td>
<td class="gt_row gt_right">0.00</td></tr>
    <tr><td class="gt_row gt_left gt_striped">year_ns_1</td>
<td class="gt_row gt_right gt_striped">8.62</td>
<td class="gt_row gt_right gt_striped">3.47</td>
<td class="gt_row gt_right gt_striped">2.49</td>
<td class="gt_row gt_right gt_striped">0.01</td></tr>
    <tr><td class="gt_row gt_left">year_ns_2</td>
<td class="gt_row gt_right">3.76</td>
<td class="gt_row gt_right">2.96</td>
<td class="gt_row gt_right">1.27</td>
<td class="gt_row gt_right">0.20</td></tr>
    <tr><td class="gt_row gt_left gt_striped">year_ns_3</td>
<td class="gt_row gt_right gt_striped">8.13</td>
<td class="gt_row gt_right gt_striped">4.21</td>
<td class="gt_row gt_right gt_striped">1.93</td>
<td class="gt_row gt_right gt_striped">0.05</td></tr>
    <tr><td class="gt_row gt_left">year_ns_4</td>
<td class="gt_row gt_right">6.81</td>
<td class="gt_row gt_right">2.40</td>
<td class="gt_row gt_right">2.84</td>
<td class="gt_row gt_right">0.00</td></tr>
    <tr><td class="gt_row gt_left gt_striped">age_ns_1</td>
<td class="gt_row gt_right gt_striped">45.17</td>
<td class="gt_row gt_right gt_striped">4.19</td>
<td class="gt_row gt_right gt_striped">10.77</td>
<td class="gt_row gt_right gt_striped">0.00</td></tr>
    <tr><td class="gt_row gt_left">age_ns_2</td>
<td class="gt_row gt_right">38.45</td>
<td class="gt_row gt_right">5.08</td>
<td class="gt_row gt_right">7.57</td>
<td class="gt_row gt_right">0.00</td></tr>
    <tr><td class="gt_row gt_left gt_striped">age_ns_3</td>
<td class="gt_row gt_right gt_striped">34.24</td>
<td class="gt_row gt_right gt_striped">4.38</td>
<td class="gt_row gt_right gt_striped">7.81</td>
<td class="gt_row gt_right gt_striped">0.00</td></tr>
    <tr><td class="gt_row gt_left">age_ns_4</td>
<td class="gt_row gt_right">48.68</td>
<td class="gt_row gt_right">10.57</td>
<td class="gt_row gt_right">4.60</td>
<td class="gt_row gt_right">0.00</td></tr>
    <tr><td class="gt_row gt_left gt_striped">age_ns_5</td>
<td class="gt_row gt_right gt_striped">6.56</td>
<td class="gt_row gt_right gt_striped">8.37</td>
<td class="gt_row gt_right gt_striped">0.78</td>
<td class="gt_row gt_right gt_striped">0.43</td></tr>
  </tbody>
  
  
</table>
</div>
```

### Utilizando mgcv


```r

parsnip::gen_additive_mod() %>%
  parsnip::set_engine("mgcv")  %>%
  parsnip::set_mode("regression") %>%
  assign(
    "gam_engine",
    .,
    envir = .GlobalEnv
  )

workflows::workflow() %>% 
  workflows::add_variables(
    outcomes = wage,
    predictors = c(year,age,education)
  ) %>% 
  workflows::add_model(
    gam_engine, 
    formula = wage ~ s(year,k=4)  + s(age,k=5) + education
  ) %>% 
  generics::fit(data = Wage) %>% 
  assign(
    "model_gam",
    .,
    envir = .GlobalEnv
  )


gam_engine %>%
  generics::fit(
    wage ~ s(age, k = 5) + education, 
    data = Wage
) %>%
assign(
  "gam_m1",
  .,
  envir = .GlobalEnv
)


gam_engine %>%
  parsnip::fit(
    wage ~ year + s(age, k = 5) + education, 
    data = Wage
) %>%
assign(
  "gam_m2",
  .,
  envir = .GlobalEnv
)


anova(
  workflowsets::extract_fit_engine(gam_m1),
  workflowsets::extract_fit_engine(gam_m2),
  workflowsets::extract_fit_engine(model_gam)
)
#> Analysis of Deviance Table
#> 
#> Model 1: wage ~ s(age, k = 5) + education
#> Model 2: wage ~ year + s(age, k = 5) + education
#> Model 3: wage ~ s(year, k = 4) + s(age, k = 5) + education
#>   Resid. Df Resid. Dev      Df Deviance
#> 1    2991.2    3717439                 
#> 2    2990.2    3700651 0.98492  16788.8
#> 3    2990.1    3700461 0.14262    189.5
```

### Regresiones locales



```r

gam_engine %>%
  parsnip::fit(
    wage ~ year + gam::lo(year,age,span = 0.5) + education, 
    data = Wage
) %>%
assign(
  "gam_lo",
  .,
  envir = .GlobalEnv
)
```

### Clasificación



```r

parsnip::gen_additive_mod() %>%
  parsnip::set_mode('classification') %>%
  parsnip::set_engine("mgcv") %>%
  assign(
    "gam_clas_engine",
    .,
    envir = .GlobalEnv
  )


Wage %<>%
  tidytable::mutate.(
    wage_dis = as.factor(wage > 250)
  )

gam_clas_engine %>%
  parsnip::fit(
    wage_dis ~ year + s(age,k=5) + education,
    family = binomial,
    data = Wage
) %>%
assign(
  "gam.lr.s",
  .,
  envir = .GlobalEnv
)

Wage %>%
  tidytable::filter.(
    education != '1. < HS Grad'
  ) %>%
  assign(
    "wage_filter",
    .,
    envir = .GlobalEnv
  )

gam_clas_engine %>%
  parsnip::fit(
    wage_dis ~ year + s(age,k=5) + education,
    family = binomial,
    data = wage_filter
) %>%
assign(
  "gam.lr.F",
  .,
  envir = .GlobalEnv
)

```

