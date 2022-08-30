# HappyDay
using System;
using System.Linq;

namespace Urodziny
{
	public static class Program
	{
		public static void Main()
		{
			Console.Write("Podaj datę urodzenia: ");
			DateTime dataUr = DateTime.Parse(Console.ReadLine());
			DateTime date = DateTime.Now;
			DateTime nastUrodziny = DateTime.Parse(dataUr.Day + " " + dataUr.Month + " " + date.Year);
			int dniDoUrodzin = (int)(nastUrodziny - date).TotalDays;
			int dniDoUrodzin1 = (int)(nastUrodziny.AddYears(1) - date).TotalDays;
			double ileLat = (double)(date - dataUr).TotalDays / 365.25;
			Console.WriteLine("================================");
			Console.WriteLine("\nPełna data Twojego urodzenia to: ");
			Console.ForegroundColor = ConsoleColor.Green;
			Console.WriteLine(dataUr.ToString("dddd, dd.MMMM.yyyy") + "rok");
			Console.ResetColor();
			Console.WriteLine("\nŻyjesz już {0} dni, {1} minut i {2} sekund", (int)(date - dataUr).TotalDays, 
			(int)(date - dataUr).TotalMinutes, (int)(date - dataUr).TotalSeconds);
			
			if(dniDoUrodzin > 0)
			{
				Console.WriteLine("\nMasz {0} lat i za {1} dni bedziesz obchodził {2} urodziny.\n\n", 
				(int)ileLat, dniDoUrodzin, Math.Ceiling(ileLat));
			}
			else if(dniDoUrodzin == 0)
			{
				Console.ForegroundColor = ConsoleColor.Green;
				Console.WriteLine("\n{0} lat właśnie Ci stukneło. Wszystkiego najlepszego!", 
				(int)ileLat);
			}
			else
			{
				Console.WriteLine("\nMasz {0} lat i za {1} dni bedziesz obchodził {2} urodziny.\n\n", 
				(int)ileLat, dniDoUrodzin1 + 1, Math.Ceiling(ileLat));
			}
		}
	}
}
