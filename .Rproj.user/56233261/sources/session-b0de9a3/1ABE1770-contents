# server.R

library(shiny)
library(DT)

server <- function(input, output, session) {
  
  # Reactive function to read uploaded data
  uploaded_data <- reactive({
    req(input$file)
    delimiter <- switch(input$delimiter, "," = ",", "Tab" = "\t", "Semicolon" = ";")
    read.table(input$file$datapath, sep = delimiter, header = input$header)
  })
  
  # Display the uploaded data in a table
  output$table <- renderDT({
    DT::datatable(uploaded_data())
  })
  
  # Event to handle data upload wizard
  observeEvent(input$uploadBtn, {
    # Perform any additional processing if needed
    # Update the main table with the new data
    updateDTOutput(session, "table")
  })
  
}

