import xarray as xr
import matplotlib.pyplot as plt
ds=xr.open_dataset("E:\\IISC\\kerala.nc")
print(ds)
print("variable_file",list(ds.data_vars))
variable_file =['t2m']
temp=ds['t2m'].sel(latitude=13, longitude=77.5, method="nearest")
annual_mean_temp = temp.resample(valid_time='1YE').mean() 

plt.figure(figsize=(12,6))
temp.plot(label='Daily Temperature')
annual_mean_temp.plot(color='red', label='Annual Mean Temperature')
plt.title("Temperature Time Series with Annual Mean")
plt.xlabel('Year')
plt.ylabel('Temperature [K]')
plt.legend()
plt.grid(True)
plt.show()
