<template>
    <div class="content container d-flex flex-column justify-content-center">
        <form class="p-3" @submit.prevent="handleSubmit">
            <div>
                <label class="form-label">Facility name</label>
                <input type="text" class="form-control" v-model="facility_name" />
            </div>
            <div class="mt-3">
                <label class="form-label">Manager name</label>
                <input type="text" class="form-control" v-model="manager_name" />
            </div>
            <div class="mt-3">
                <label class="form-label">Address</label>
                <input type="text" class="form-control" v-model="address" />
            </div>
            <div class="mt-3">
                <label class="form-label">Phone number</label>
                <input type="number" class="form-control" v-model="phone_number" />
            </div>
            <div class="mt-3 row">
                <label class="form-label">Problem location</label>
                <div class="col">
                    <input type="checkbox" class="form-check-input" v-model="printer">
                    <label class="form-check-label ms-1">Printer</label>
                </div>
                <div class="col">
                    <input type="checkbox" class="form-check-input" v-model="pc">
                    <label class="form-check-label ms-1">PC</label>
                </div>
                <div class="col">
                    <input type="checkbox" class="form-check-input" v-model="camera">
                    <label class="form-check-label ms-1">Camera</label>
                </div>
                <div class="col">
                    <input type="checkbox" class="form-check-input" v-model="network">
                    <label class="form-check-label ms-1">Netweork</label>
                </div>
            </div>
            <div class="mt-3">
                <label class="form-label">Problem description</label>
                <textarea class="form-control" v-model="problem_description"></textarea>
            </div>
            <button class="btn btn-danger mt-3">Submit</button>
        </form>
    </div>
</template>

<script>
import emailjs from '@emailjs/browser';
export default{
    data(){
        return{
            facility_name: '',
            manager_name: '',
            address: '',
            phone_number: null,
            problem_location: '',
            problem_description: '',

            printer: false,
            pc: false,
            camera: false,
            network: false,
        }
    },
    methods: {
        handleSubmit(e) {
            console.log('facility_name: ', this.facility_name)
            console.log('manager_name: ', this.manager_name)
            console.log('address: ', this.address)
            console.log('phone_number: ', this.phone_number)
            console.log('problem_description: ', this.problem_description)

            const service_id = "service_yo329y5";
            const template_id = "template_awscbii";
            const public_key = 'nkhiPXCZ3Os0At9pg';

            
            
            if(this.printer){ this.problem_location += "printer, " }
            if(this.pc){ this.problem_location += "pc, " }
            if(this.camera){ this.problem_location += "camera, " }
            if(this.network){ this.problem_location += "network, " }

            console.log(this.problem_location)

            var message = "I'm sending you this email to inform you of a problem in '" + this.problem_location + "' , and my problem is: " + this.problem_description

            var templateParams = {
                from_name: this.facility_name,
                cc: "Report a problem",
                bcc: "Report a problem",
                message: message
            };
            emailjs.send(
                service_id, template_id, templateParams, public_key
                ).then(res => {
                    console.log('Email successfully sent!')
                })
                // Handle errors here however you like, or use a React error boundary
                .catch(err => console.error('Oh well, you failed. Here some thoughts on the error that occured:', err))
                
            this.facility_name = '',
            this.manager_name = '',
            this.address = '',
            this.phone_number = null,
            this.problem_location = '',
            this.problem_description = '',
            this.printer = false,
            this.pc = false,
            this.camera = false,
            this.network = false
        },
    }
}
</script>

<style>
    .content{
        height: calc(100vh - 20px);
    }
    form{
        /* background-color: rgba(255,220,69,0.4); */
        background-color: rgba(193,193,193,0.4);
        border-radius: 30px;
    }
</style>