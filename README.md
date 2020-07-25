# yes
Thing
(function() {
    'use strict';
    window.configElements = []
    //==BEGIN UI BUILDING==
    window.overlay = document.createElement("div")
    window.overlay.style.width = "100vw"
    window.overlay.style.height = "100vh"
    window.overlay.style.zIndex = "1"
    window.overlay.style.position = "fixed"
    window.overlay.style.visibility = "hidden"
    window.overlay.id = "overlay"
    document.body.prepend(window.overlay)
    function BuildMenuEntry (name, info, id, configpane) {
        window.entry = document.createElement("div")
        window.tickbox = document.createElement("input")
        window.tickbox.type = "checkbox"
        window.tickbox.id = id
        window.configElements.push(id)
        window.entry.appendChild(window.tickbox)
        window.window.label = document.createElement("label")
        window.label.innerText = name
        window.entry.appendChild(window.label)
        if (configpane != undefined) {
            window.configbutton = document.createElement("button")
            window.configbutton.innerText = "Configure"
            window.configbutton.style.marginLeft = "7px"
            window.configbutton.style.border = "1px solid #5f5f5f"
            window.configbutton.style.boxShadow = "inset 0 0 5px rgba(0, 0, 0, 0.6)"
            window.configbutton.style.backgroundColor = "rgb(39, 39, 39)"
            window.configbutton.style.color = "#f9a619"
            window.configbutton.style.borderRadius = "3px"
            window.configbutton.onclick = function () {
                if (document.getElementById(configpane).style.visibility == "unset") {
                    document.getElementById(configpane).style.visibility = "hidden"
                } else {
                    document.getElementById(configpane).style.visibility = "unset"
                }
            }
            window.entry.appendChild(window.configbutton)
        }
        window.desc = document.createElement("p")
        window.desc.innerHTML = info;
        window.entry.appendChild(window.desc)
        return window.entry
    }
    function RenderPane(name, id, width, height, margintop, marginleft) {
        window.pane = document.createElement("div")
        window.pane.style.width = width
        window.pane.style.height = height
        window.pane.style.position = "absolute"
        window.pane.style.marginTop = margintop
        window.pane.style.marginLeft = marginleft
        window.pane.style.border = "1px solid rgb(95, 95, 95)"
        window.pane.style.borderRadius = "3px"
        window.pane.style.backgroundColor = "rgb(39, 39, 39)"
        window.pane.style.overflow = "hidden"
        window.pane.style.color = "rgb(249, 166, 25)"
        window.pane.style.textAlign = "center"
        window.pane.style.overflowY = "scroll"
        window.pane.id = id
        window.panetitle = document.createElement("h1")
        window.panetitle.innerText = name
        window.pane.appendChild(window.panetitle)
        window.pane.appendChild(document.createElement("hr"))
        document.getElementById("overlay").appendChild(window.pane)
    }
