# Lab-Assignment-3
using System;
using System.Xml;

class Program
{
    static void Main()
    {
        XmlWriterSettings settings = new XmlWriterSettings();
        settings.Indent = true;  
        settings.IndentChars = "\t";  
        using (XmlWriter w = XmlWriter.Create("GPS.xml", settings))
        {
            w.WriteStartDocument();

            w.WriteStartElement("GPS_Log");

            w.WriteStartElement("Position");
            w.WriteAttributeString("DateTime", "1/26/2017 5:08:59 PM");

            w.WriteElementString("x", "65.8973342");
            w.WriteElementString("y", "72.3452346");

            w.WriteStartElement("SatteliteInfo");
            w.WriteElementString("Speed", "40");
            w.WriteElementString("NoSatt", "7");
            w.WriteEndElement(); 
            w.WriteEndElement();

            w.WriteStartElement("Image");
            w.WriteAttributeString("Resolution", "1024x800");
            w.WriteElementString("Path", @"\images\1.jpg");

            w.WriteEndElement();

            w.WriteEndElement();

            w.WriteEndDocument();
        }
        Console.WriteLine("Generated XML file content:");
        XmlDocument doc = new XmlDocument();
        doc.Load("GPS.xml");  

        Console.WriteLine(doc.OuterXml);
    }
}
