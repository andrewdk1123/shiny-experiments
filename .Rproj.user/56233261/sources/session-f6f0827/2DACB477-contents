# ui.R

library(shiny)
library(shinydashboard)
library(shinyjs)
library(DT)

ui <- dashboardPage(
  dashboardHeader(
    title = "Shiny Experiments",
    dropdownMenu(
      type = "message",
      messageItem(from = "Admin", message = "Welcome to the app!")
    )
  ),
  dashboardSidebar(
    sidebarMenu(
      menuItem("Upload Data", tabName = "upload", icon = icon("upload")),
      menuItem("Data Manipulation", tabName = "manipulate", icon = icon("table"),
               menuSubItem("Sub Item 1", tabName = "subitem1"),
               menuSubItem("Sub Item 2", tabName = "subitem2")),
      menuItem("Data Visualization", tabName = "visualize", icon = icon("chart-pie"),
               menuSubItem("Sub Item 1", tabName = "subitem3"),
               menuSubItem("Sub Item 2", tabName = "subitem4")),
      menuItem("Data Analysis", tabName = "analyze", icon = icon("calculator"),
               menuSubItem("Sub Item 1", tabName = "subitem5"),
               menuSubItem("Sub Item 2", tabName = "subitem6"))
    )
  ),
  dashboardBody(
    useShinyjs(),  # Initialize shinyjs
    tabItems(
      tabItem(
        tabName = "upload",
        fluidRow(
          box(
            title = "Data Upload",
            fileInput("file", "Choose File",
                      accept = c(".csv", ".tsv", ".xlsx", ".xls")),
            selectInput("delimiter", "Select Delimiter",
                        choices = c("Comma" = ",", "Tab" = "\t", "Semicolon" = ";"),
                        selected = ","),
            checkboxInput("header", "Data contains header", TRUE),
            actionButton("uploadBtn", "Upload Data")
          )
        )
      ),
      tabItem(
        tabName = "analysis",
        fluidRow(
          box(
            title = "Uploaded Data",
            status = "info",
            solidHeader = TRUE,
            width = 12,
            DTOutput("table")
          )
        )
      )
    )
  )
)
