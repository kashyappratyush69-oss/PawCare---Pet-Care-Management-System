# PawCare---Pet-Care-Management-System[inddex.html](https://github.com/user-attachments/files/26564654/inddex.html)
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PawCare - Pet Care Management System</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 100%);
            min-height: 100vh;
            padding: 20px;
        }
        .container {
            max-width: 1400px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
            overflow: hidden;
        }
        .header {
            background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 100%);
            color: #5a3e2b;
            padding: 30px;
            text-align: center;
        }
        .stats-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
            gap: 20px;
            padding: 30px;
            background: #fff5f0;
        }
        .stat-card { background: white; padding: 20px; border-radius: 15px; text-align: center; }
        .stat-card h3 { font-size: 2em; color: #ff6b6b; }
        .tabs { display: flex; gap: 10px; padding: 20px 30px 0 30px; flex-wrap: wrap; }
        .tab-btn { padding: 12px 24px; border: none; background: #ecf0f1; cursor: pointer; border-radius: 10px 10px 0 0; font-weight: 600; }
        .tab-btn.active { background: #ff9a9e; color: #5a3e2b; }
        .tab-content { display: none; padding: 30px; }
        .tab-content.active { display: block; }
        .form-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; }
        .form-group { margin-bottom: 15px; }
        .form-group label { display: block; margin-bottom: 8px; font-weight: 500; color: #555; }
        .form-group input, .form-group select, .form-group textarea { width: 100%; padding: 12px; border: 2px solid #e0e0e0; border-radius: 10px; }
        .btn { padding: 12px 28px; border: none; border-radius: 10px; cursor: pointer; font-weight: 600; margin-right: 10px; }
        .btn-primary { background: #ff9a9e; color: #5a3e2b; }
        .btn-primary:hover { background: #ff7a7e; transform: translateY(-2px); }
        .btn-success { background: #27ae60; color: white; }
        .btn-danger { background: #e74c3c; color: white; }
        .btn-warning { background: #f39c12; color: white; }
        .search-bar { margin-bottom: 20px; }
        .search-bar input { width: 100%; padding: 12px; border: 2px solid #e0e0e0; border-radius: 10px; }
        .table-section { overflow-x: auto; }
        table { width: 100%; border-collapse: collapse; }
        th { background: #ff9a9e; color: #5a3e2b; padding: 12px; text-align: left; }
        td { padding: 12px; border-bottom: 1px solid #ecf0f1; }
        .vaccine-upcoming { background: #f39c12; color: white; padding: 4px 12px; border-radius: 20px; font-size: 0.85em; display: inline-block; }
        .vaccine-done { background: #27ae60; color: white; padding: 4px 12px; border-radius: 20px; font-size: 0.85em; display: inline-block; }
        .pet-card { display: inline-block; margin: 5px; }
        .emergency { background: #e74c3c; color: white; padding: 10px; border-radius: 10px; text-align: center; margin-top: 20px; }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1><i class="fas fa-paw"></i> PawCare - Pet Care Management System</h1>
            <p>Loving Care for Your Furry Friends</p>
        </div>
        <div class="stats-container">
            <div class="stat-card"><i class="fas fa-dog"></i><h3 id="totalPets">0</h3><p>Total Pets</p></div>
            <div class="stat-card"><i class="fas fa-user"></i><h3 id="totalOwners">0</h3><p>Pet Owners</p></div>
            <div class="stat-card"><i class="fas fa-syringe"></i><h3 id="upcomingVaccines">0</h3><p>Upcoming Vaccines</p></div>
            <div class="stat-card"><i class="fas fa-calendar-check"></i><h3 id="todayAppointments">0</h3><p>Today's Appointments</p></div>
        </div>
        <div class="tabs">
            <button class="tab-btn active" onclick="showTab('pets')">🐕 Pets</button>
            <button class="tab-btn" onclick="showTab('appointments')">📅 Appointments</button>
            <button class="tab-btn" onclick="showTab('vaccinations')">💉 Vaccinations</button>
            <button class="tab-btn" onclick="showTab('grooming')">✂️ Grooming</button>
            <button class="tab-btn" onclick="showTab('medicine')">💊 Medicine</button>
        </div>
        <div id="petsTab" class="tab-content active">
            <div class="form-section"><h3>Register New Pet</h3><div class="form-grid">
                <div class="form-group"><label>Pet Name *</label><input type="text" id="petName" placeholder="Pet name"></div>
                <div class="form-group"><label>Pet Type</label><select id="petType"><option>Dog</option><option>Cat</option><option>Bird</option><option>Rabbit</option><option>Other</option></select></div>
                <div class="form-group"><label>Breed</label><input type="text" id="petBreed" placeholder="Breed"></div>
                <div class="form-group"><label>Age (Years)</label><input type="number" id="petAge" placeholder="Age"></div>
                <div class="form-group"><label>Weight (kg)</label><input type="number" id="petWeight" placeholder="Weight"></div>
                <div class="form-group"><label>Owner Name *</label><input type="text" id="ownerName" placeholder="Owner name"></div>
                <div class="form-group"><label>Owner Phone *</label><input type="tel" id="ownerPhone" placeholder="Contact number"></div>
                <div class="form-group"><label>Owner Email</label><input type="email" id="ownerEmail" placeholder="Email"></div>
                <div class="form-group"><label>Address</label><textarea id="ownerAddress" rows="2" placeholder="Address"></textarea></div>
                <div class="form-group"><label>Emergency Contact</label><input type="tel" id="emergencyContact" placeholder="Emergency number"></div>
            </div><button class="btn btn-primary" onclick="addPet()">Register Pet</button></div>
            <div class="search-bar"><input type="text" id="searchPet" placeholder="🔍 Search by pet name, owner..." onkeyup="searchPets()"></div>
            <div class="table-section">\n<table><thead><tr><th>ID</th><th>Pet Details</th><th>Owner</th><th>Age/Weight</th><th>Actions</th></tr></thead><tbody id="petsTableBody"></tbody></table></div>
        </div>
        <div id="appointmentsTab" class="tab-content">
            <div class="form-section"><h3>Book Appointment</h3><div class="form-grid">
                <div class="form-group"><label>Select Pet</label><select id="appointmentPet"></select></div>
                <div class="form-group"><label>Appointment Date</label><input type="datetime-local" id="appointmentDate"></div>
                <div class="form-group"><label>Reason</label><select id="appointmentReason"><option>Regular Checkup</option><option>Vaccination</option><option>Sick Visit</option><option>Grooming</option><option>Emergency</option></select></div>
                <div class="form-group"><label>Notes</label><textarea id="appointmentNotes" rows="2" placeholder="Any special notes"></textarea></div>
            </div><button class="btn btn-primary" onclick="addAppointment()">Book Appointment</button></div>
            <div class="table-section"><table><thead><tr><th>Pet Name</th><th>Owner</th><th>Date & Time</th><th>Reason</th><th>Status</th><th>Action</th></tr></thead><tbody id="appointmentsTableBody"></tbody></table></div>
        </div>
        <div id="vaccinationsTab" class="tab-content">
            <div class="form-section"><h3>Add Vaccination Record</h3><div class="form-grid">
                <div class="form-group"><label>Select Pet</label><select id="vaccinePet"></select></div>
                <div class="form-group"><label>Vaccine Name</label><input type="text" id="vaccineName" placeholder="e.g., Rabies, Parvo"></div>
                <div class="form-group"><label>Date Given</label><input type="date" id="vaccineDate"></div>
                <div class="form-group"><label>Next Due Date</label><input type="date" id="vaccineDue"></div>
            </div><button class="btn btn-primary" onclick="addVaccination()">Add Record</button></div>
            <div class="table-section"><table><thead><tr><th>Pet</th><th>Vaccine</th><th>Date Given</th><th>Next Due</th><th>Status</th></tr></thead><tbody id="vaccinationsTableBody"></tbody></table></div>
            <div class="emergency" id="vaccineReminder"></div>
        </div>
        <div id="groomingTab" class="tab-content">
            <div class="form-section"><h3>Grooming Services</h3><div class="form-grid">
                <div class="form-group"><label>Select Pet</label><select id="groomingPet"></select></div>
                <div class="form-group"><label>Service Type</label><select id="groomingService"><option>Bath & Brush</option><option>Hair Cut</option><option>Nail Trimming</option><option>Full Grooming</option></select></div>
                <div class="form-group"><label>Booking Date</label><input type="date" id="groomingDate"></div>
            </div><button class="btn btn-primary" onclick="addGrooming()">Book Grooming</button></div>
            <div class="table-section"><table><thead><tr><th>Pet</th><th>Service</th><th>Date</th><th>Status</th><th>Action</th></tr></thead><tbody id="groomingTableBody"></tbody></table></div>
        </div>
        <div id="medicineTab" class="tab-content">
            <div class="form-section"><h3>Medicine Inventory</h3><div class="form-grid">
                <div class="form-group"><label>Medicine Name</label><input type="text" id="medicineName"></div>
                <div class="form-group"><label>Stock Quantity</label><input type="number" id="medicineStock"></div>
                <div class="form-group"><label>Price (₹)</label><input type="number" id="medicinePrice"></div>
            </div><button class="btn btn-primary" onclick="addMedicine()">Add Medicine</button></div>
            <div class="table-section"><table><thead><tr><th>Medicine</th><th>Stock</th><th>Price</th><th>Actions</th></tr></thead><tbody id="medicineTableBody"></tbody></table></div>
        </div>
    </div>
    <script>
        let pets = JSON.parse(localStorage.getItem('petcare_pets')) || [];
        let appointments = JSON.parse(localStorage.getItem('petcare_appointments')) || [];
        let vaccinations = JSON.parse(localStorage.getItem('petcare_vaccinations')) || [];
        let groomings = JSON.parse(localStorage.getItem('petcare_groomings')) || [];
        let medicines = JSON.parse(localStorage.getItem('petcare_medicines')) || [];
        let nextPetId = pets.length>0?Math.max(...pets.map(p=>p.id))+1:1;
        if(pets.length===0){ pets=[{id:1,name:"Max",type:"Dog",breed:"Golden Retriever",age:3,weight:28,owner:"Rajesh",phone:"9876543210",email:"raj@email.com",address:"Delhi",emergency:"9876543219"}]; localStorage.setItem('petcare_pets',JSON.stringify(pets)); }
        function showTab(tab){ document.querySelectorAll('.tab-content').forEach(t=>t.classList.remove('active')); document.querySelectorAll('.tab-btn').forEach(b=>b.classList.remove('active')); document.getElementById(tab+'Tab').classList.add('active'); event.target.classList.add('active'); refreshAll(); }
        function refreshAll(){ displayPets(); displayAppointments(); displayVaccinations(); displayGrooming(); displayMedicine(); updateStats(); loadPetDropdowns(); checkVaccineReminders(); }
        function addPet(){ let name=document.getElementById('petName').value.trim(); let type=document.getElementById('petType').value; let breed=document.getElementById('petBreed').value.trim(); let age=parseInt(document.getElementById('petAge').value); let weight=parseInt(document.getElementById('petWeight').value); let owner=document.getElementById('ownerName').value.trim(); let phone=document.getElementById('ownerPhone').value.trim(); let email=document.getElementById('ownerEmail').value; let address=document.getElementById('ownerAddress').value; let emergency=document.getElementById('emergencyContact').value; if(!name||!owner||!phone){ alert('Please fill required fields!'); return; } pets.push({id:nextPetId++,name,type,breed,age,weight,owner,phone,email,address,emergency}); localStorage.setItem('petcare_pets',JSON.stringify(pets)); displayPets(); updateStats(); loadPetDropdowns(); clearPetForm(); alert('Pet registered!'); }
        function displayPets(){ let tbody=document.getElementById('petsTableBody'); tbody.innerHTML=''; pets.forEach(p=>{ let row=tbody.insertRow(); row.innerHTML=`<td>${p.id}</td><td><strong>${p.name}</strong><br><small>${p.type} | ${p.breed||'-'}</small></td><td>${p.owner}<br><small>📞 ${p.phone}</small></td><td>${p.age} yrs | ${p.weight} kg</td><td><button class="btn-danger" onclick="deletePet(${p.id})">Delete</button></td>`; }); }
        function deletePet(id){ if(confirm('Delete pet record?')){ pets=pets.filter(p=>p.id!==id); localStorage.setItem('petcare_pets',JSON.stringify(pets)); displayPets(); updateStats(); loadPetDropdowns(); } }
        function addAppointment(){ let petId=parseInt(document.getElementById('appointmentPet').value); let date=document.getElementById('appointmentDate').value; let reason=document.getElementById('appointmentReason').value; let notes=document.getElementById('appointmentNotes').value; if(!petId||!date){ alert('Select pet and date!'); return; } appointments.push({id:appointments.length+1,petId,date,reason,notes,status:"Scheduled"}); localStorage.setItem('petcare_appointments',JSON.stringify(appointments)); displayAppointments(); alert('Appointment booked!'); }
        function displayAppointments(){ let tbody=document.getElementById('appointmentsTableBody'); tbody.innerHTML=''; appointments.forEach(a=>{ let pet=pets.find(p=>p.id===a.petId); if(pet){ let row=tbody.insertRow(); row.innerHTML=`<td>${pet.name}</td><td>${pet.owner}</td><td>${new Date(a.date).toLocaleString()}</td><td>${a.reason}</td><td><span class="status-confirmed">${a.status}</span></td><td><button class="btn-success" onclick="completeAppointment(${a.id})">Complete</button><button class="btn-danger" onclick="deleteAppointment(${a.id})">Cancel</button></td>`; } }); }
        function completeAppointment(id){ let a=appointments.find(a=>a.id===id); if(a){ a.status="Completed"; localStorage.setItem('petcare_appointments',JSON.stringify(appointments)); displayAppointments(); updateStats(); } }
        function deleteAppointment(id){ appointments=appointments.filter(a=>a.id!==id); localStorage.setItem('petcare_appointments',JSON.stringify(appointments)); displayAppointments(); }
        function addVaccination(){ let petId=parseInt(document.getElementById('vaccinePet').value); let name=document.getElementById('vaccineName').value.trim(); let date=document.getElementById('vaccineDate').value; let due=document.getElementById('vaccineDue').value; if(!petId||!name||!date){ alert('Fill required fields!'); return; } vaccinations.push({id:vaccinations.length+1,petId,vaccine:name,date,due}); localStorage.setItem('petcare_vaccinations',JSON.stringify(vaccinations)); displayVaccinations(); checkVaccineReminders(); }
        function displayVaccinations(){ let tbody=document.getElementById('vaccinationsTableBody'); tbody.innerHTML=''; vaccinations.forEach(v=>{ let pet=pets.find(p=>p.id===v.petId); if(pet){ let dueDate=new Date(v.due); let today=new Date(); let isUpcoming=dueDate>today&&dueDate-today<7*24*60*60*1000; let status=isUpcoming?'Upcoming':'Done'; let row=tbody.insertRow(); row.innerHTML=`<td>${pet.name}</td><td>${v.vaccine}</td><td>${v.date}</td><td>${v.due}</td><td><span class="${isUpcoming?'vaccine-upcoming':'vaccine-done'}">${status}</span></td>`; } }); }
        function checkVaccineReminders(){ let upcoming=[]; vaccinations.forEach(v=>{ let dueDate=new Date(v.due); let today=new Date(); if(dueDate>today&&dueDate-today<7*24*60*60*1000){ let pet=pets.find(p=>p.id===v.petId); if(pet) upcoming.push(`${pet.name} - ${v.vaccine} due on ${v.due}`); } }); let reminderDiv=document.getElementById('vaccineReminder'); if(upcoming.length>0){ reminderDiv.innerHTML=`<i class="fas fa-bell"></i> Vaccine Reminder: ${upcoming.join(', ')}`; }else{ reminderDiv.innerHTML='<i class="fas fa-check-circle"></i> No upcoming vaccines due this week!'; } }
        function addGrooming(){ let petId=parseInt(document.getElementById('groomingPet').value); let service=document.getElementById('groomingService').value; let date=document.getElementById('groomingDate').value; if(!petId||!date){ alert('Select pet and date!'); return; } groomings.push({id:groomings.length+1,petId,service,date,status:"Scheduled"}); localStorage.setItem('petcare_groomings',JSON.stringify(groomings)); displayGrooming(); alert('Grooming booked!'); }
        function displayGrooming(){ let tbody=document.getElementById('groomingTableBody'); tbody.innerHTML=''; groomings.forEach(g=>{ let pet=pets.find(p=>p.id===g.petId); if(pet){ let row=tbody.insertRow(); row.innerHTML=`<td>${pet.name}</td><td>${g.service}</td><td>${g.date}</td><td><span class="status-confirmed">${g.status}</span></td><td><button class="btn-success" onclick="completeGrooming(${g.id})">Complete</button><button class="btn-danger" onclick="deleteGrooming(${g.id})">Cancel</button></td>`; } }); }
        function completeGrooming(id){ let g=groomings.find(g=>g.id===id); if(g){ g.status="Completed"; localStorage.setItem('petcare_groomings',JSON.stringify(groomings)); displayGrooming(); } }
        function deleteGrooming(id){ groomings=groomings.filter(g=>g.id!==id); localStorage.setItem('petcare_groomings',JSON.stringify(groomings)); displayGrooming(); }
        function addMedicine(){ let name=document.getElementById('medicineName').value.trim(); let stock=parseInt(document.getElementById('medicineStock').value); let price=parseInt(document.getElementById('medicinePrice').value); if(!name){ alert('Enter medicine name!'); return; } medicines.push({id:medicines.length+1,name,stock,price}); localStorage.setItem('petcare_medicines',JSON.stringify(medicines)); displayMedicine(); clearMedicineForm(); }
        function displayMedicine(){ let tbody=document.getElementById('medicineTableBody'); tbody.innerHTML=''; medicines.forEach(m=>{ let row=tbody.insertRow(); row.innerHTML=`<td>${m.name}</td><td>${m.stock}</td><td>₹${m.price}</td><td><button class="btn-danger" onclick="deleteMedicine(${m.id})">Delete</button></td>`; }); }
        function deleteMedicine(id){ medicines=medicines.filter(m=>m.id!==id); localStorage.setItem('petcare_medicines',JSON.stringify(medicines)); displayMedicine(); }
        function updateStats(){ document.getElementById('totalPets').textContent=pets.length; document.getElementById('totalOwners').textContent=[...new Set(pets.map(p=>p.owner))].length; let upcomingVaccines=vaccinations.filter(v=>new Date(v.due)>new Date()&&new Date(v.due)-new Date()<7*24*60*60*1000).length; document.getElementById('upcomingVaccines').textContent=upcomingVaccines; let today=new Date().toISOString().split('T')[0]; let todayAppts=appointments.filter(a=>a.date.split('T')[0]===today).length; document.getElementById('todayAppointments').textContent=todayAppts; }
        function loadPetDropdowns(){ let petSelects=['appointmentPet','vaccinePet','groomingPet']; petSelects.forEach(id=>{ let select=document.getElementById(id); if(select){ select.innerHTML=''; pets.forEach(p=>{select.innerHTML+=`<option value="${p.id}">${p.name} (${p.type}) - ${p.owner}</option>`;}); } }); }
        function searchPets(){ let term=document.getElementById('searchPet').value.toLowerCase(); let filtered=pets.filter(p=>p.name.toLowerCase().includes(term)||p.owner.toLowerCase().includes(term)); let tbody=document.getElementById('petsTableBody'); tbody.innerHTML=''; filtered.forEach(p=>{ let row=tbody.insertRow(); row.innerHTML=`<td>${p.id}</td><td><strong>${p.name}</strong><br><small>${p.type} | ${p.breed||'-'}</small></td><td>${p.owner}<br><small>📞 ${p.phone}</small></td><td>${p.age} yrs | ${p.weight} kg</td><td><button class="btn-danger" onclick="deletePet(${p.id})">Delete</button>${p.emergency?`<br><small>Emergency: ${p.emergency}</small>`:''}${p.address?`<br><small>📍 ${p.address}</small>`:''}</td>`;}); }
        function clearPetForm(){ document.getElementById('petName').value=''; document.getElementById('petBreed').value=''; document.getElementById('petAge').value=''; document.getElementById('petWeight').value=''; document.getElementById('ownerName').value=''; document.getElementById('ownerPhone').value=''; document.getElementById('ownerEmail').value=''; document.getElementById('ownerAddress').value=''; document.getElementById('emergencyContact').value=''; }
        function clearMedicineForm(){ document.getElementById('medicineName').value=''; document.getElementById('medicineStock').value=''; document.getElementById('medicinePrice').value=''; }
        refreshAll();
    </script>
</body>
</html>
