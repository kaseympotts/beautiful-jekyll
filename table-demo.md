   ###
    ###  LAYOUT INHERITANCE
    ###
    ###  pages built by adding elements 
    ###  to other page layouts 
    ###

          default.html layout 
          │
          └── nice-text.html layout 
              │
              └── liquid-table.html layout
                  # see liquid table below



          ###
          ###  default.html layout
          ###

          <html>
          <head>
            <body>                                
              <header>   

              {{ content }}     

              <footer>           
            </body>  
          </html>     

          ###
          ###  {{content}}
          ###  is replaced by
          ###  whatever content
          ###  is on the page that
          ###  uses the default.html 
          ###  template 
          ###



          ###
          ### nice-text.html layout
          ###

          ---
          layout: default
          ---

          <div class="pretty-text">

          <h1> {{ page.title }} </h1>

          {{ content }}

          </div>


          ###
          ### liquid-table.html layout
          ###

          ---
          layout: nice-text
          ---

          {{ content }}

          #  liquid table starts here





    ###
    ###  LIQUID TABLE ADDED USING YAML DATA
    ###
    ###  liquid is a simple markup language that allows
    ###  web designers to separate page layouts from
    ###  page content without databases
    ###
    ###  {%  function in liquid  %}
    ###  {{  variable in liquid  }}
    ###

        ###
        ###  YAML HEADER FOR PAGE
        ###

        ---
        layout: liquid-table
        title: 'amiright?'
        reynolds:
          strengths:
          - good father
          - funny
          - dated alanis morissette
          weaknesses: 
          - singing
          - green lantern movie
          - tennis backhand 
        gosling:
          strengths: 
          - builds houses
          - is a real boy
          - never dated alanis morissette
          weaknesses: 
          - micky mouse club
          - cries a lot
          - not ryan reynolds
        ---

       ###
       ###  LIQUID TAG TABLE IN LAYOUT
       ###
       ###  HTML ELEMENTS: 
       ###  <thead> table header
       ###  <tr>  table row 
       ###  <td>  table cell (or data)
       ###  <ul> unordered list
       ###  <li> list item 
       ###

        <h2> Ryan vs Ryan </h2>

        <table id="ryan-v-ryan">

        <thead>
          <tr>
            <th>  <h3>  Ryan Reynolds  </h3>  </th>
            <th>  <h3>  Ryan Gosling  </h3>  </th>
          </tr>
        </thead>

        <tbody>
        <tr>
          <td>
            <h4>  Strengths  </h4>
            <ul>

              ###  LIQUID LOOPS WITH YAML DATA
              ###  reynolds:
              ###    strengths:
              ###    - good father
              ###    - funny
              ###    - dated alanis morissette

              {% for item in page.reynolds.strengths %}
                 <li>  {{ item }}  </li>
              {% endfor %}

              ###    LIQUID LOOP CREATES HTML CODES:
              ###    <li> good father </li>
              ###    <li> funny </li>
              ###    <li> dated alanis morissette </li>        

            </ul>
            <br>
            <h4>  Weaknessess  </h4>
            <ul>

              {% for item in page.reynolds.weaknesses %}
                 <li>  {{ item }}  </li>
              {% endfor %}

            </ul>  
          </td>
          <td>
            <h4>  Strengths  </h4>
            <ul>

              {% for item in page.gosling.strengths %}
                <li>  {{ item }}  </li>
              {% endfor %}

            </ul>
            <br>
            <h4>  Weaknessess  </h4>
            <ul>

              {% for item in page.gosling.weaknesses %}
                 <li>  {{ item }}  </li>
              {% endfor %}

            </ul>
          </td>
        </tr> 
        </table>

