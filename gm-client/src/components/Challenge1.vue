<template>
    <div>
        <div class="navbar bg-base-100">
            <a class="btn btn-ghost normal-case text-xl">Challenge One</a>
        </div>
    </div>
    <div id="container"></div>
</template>

<script>
import * as d3 from "d3";
export default {
    name: "ChallengeOne",
    components: {},
    data() {
        return {}
    },
    methods: {},
    mounted() {
        d3.csv('/temperature_daily.csv').then(data => {
            // read data in public document
            console.log("Data Accessible!")
            console.log(data)
        }).catch(error => {
            // catch error
            console.error("Error loading the CSV file", error);
        });


        const width = 1080;
        const height = 720;
        const marginTop = 20;
        const marginRight = 20;
        const marginBottom = 30;
        const marginLeft = 80;


        // Create the SVG container.
        const svg = d3.create("svg")
            .attr("width", width)
            .attr("height", height);

        // 
        const years = d3.range(1997, 2018);
        // Ensure that 'years' contains unique values
        const uniqueYears = [...new Set(years)];

        const x = d3.scaleBand()
            .domain(uniqueYears) // Only unique years
            .range([marginLeft, width - marginRight])
            .padding(0.1); // Adjust padding to control space between bands

        const months = d3.range(1, 13); // Generates an array with numbers from 1 to 12
        const monthNames = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];

        const y = d3.scaleBand()
            .domain(months) // 1 to 12 for months
            .range([height - marginBottom, marginTop])
            .padding(0.1); // Adjust padding to control space between bands

        // ... (rest of your D3 code to create the heatmap)

        // When appending the axes, use the scales like this:
        // you can change the position of x and y axis

        svg.append("g")
            .attr("transform", `translate(${marginLeft},0)`)
            .call(d3.axisLeft(y).tickFormat((d, i) => monthNames[d - 1]));

        svg.append("g")
            .attr("transform", `translate(0,${height - marginBottom})`)
            .call(d3.axisBottom(x).tickFormat(d3.format('d'))); // 'd' for decimal format



        // Append the SVG element.
        container.append(svg.node());
    }
}
</script>

<style scoped></style>