# MediAppointments

using Microsoft.EntityFrameworkCore;

public class AppointmentService
{
    private readonly ApplicationDbContext _context;

    public AppointmentService(ApplicationDbContext context)
    {
        _context = context;
    }

    public async Task<List<Appointment>> GetAppointmentsAsync()
    {
        return await _context.Appointments.ToListAsync();
    }

    public async Task CreateAppointmentAsync(Appointment appointment)
    {
        _context.Appointments.Add(appointment);
        await _context.SaveChangesAsync();
    }
}
