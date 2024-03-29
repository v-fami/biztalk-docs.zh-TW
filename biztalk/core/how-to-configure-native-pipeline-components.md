---
title: 如何設定原生管線元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: adb6b994-c20c-4f43-82c5-a07b29498cdf
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ded5fc598144edd511005d1c1cd0342253bca3a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248710"
---
# <a name="how-to-configure-native-pipeline-components"></a>如何設定原生管線元件
下列程式碼示範如何使用 `IPersistPropertyBag` 介面來設定原生管線元件。  
  
```  
    [ComponentCategory(CategoryTypes.CATID_PipelineComponent)]  
    [ComponentCategory(CategoryTypes.CATID_Any)]  
    public class PipelineComponent :   
        IBaseComponent,   
        Microsoft.BizTalk.Component.Interop.IComponent,  
        Microsoft.BizTalk.Component.Interop.IPersistPropertyBag,  
        IComponentUI  
    {  
        private string prependData  = null;  
  
        public string PrependData  
        {  
            get {  return prependData; }  
            set {  prependData = value;}  
        }  
  
        /// <summary>  
        /// IPersistPropertyBag.Load - Loads configuration property for component.  
        /// </summary>  
        /// <param name="pb">Configuration property bag.</param>  
        /// <param name="errlog">Error status (not used in this code).</param>  
        public void Load(Microsoft.BizTalk.Component.Interop.IPropertyBag pb, Int32 errlog)  
        {  
            val = (string)ReadPropertyBag(pb, "PrependData");  
            if (val != null) prependData = val;  
        }  
  
        /// <summary>  
        /// IPersistPropertyBag.Save - Saves the current component configuration into the property bag.  
        /// </summary>  
        /// <param name="pb">Configuration property bag.</param>  
        /// <param name="fClearDirty">Not used.</param>  
        /// <param name="fSaveAllProperties">Not used.</param>  
        public void Save(Microsoft.BizTalk.Component.Interop.IPropertyBag pb, Boolean fClearDirty, Boolean fSaveAllProperties)  
        {  
            val = (object)prependData;  
            WritePropertyBag(pb, "PrependData", val);  
        }  
  
        /// <summary>  
        /// Reads property value from property bag.  
        /// </summary>  
        /// <param name="pb">Property bag.</param>  
        /// <param name="propName">Name of property.</param>  
        /// <returns>Value of the property.</returns>  
        private static object ReadPropertyBag(Microsoft.BizTalk.Component.Interop.IPropertyBag pb, string propName)  
        {  
            object val = null;  
            try  
            {  
                pb.Read(propName,out val,0);  
            }  
  
            catch(ArgumentException)  
            {  
                return val;  
            }  
            catch(Exception ex)  
            {  
                throw new ApplicationException( ex.Message);  
            }  
            return val;  
        }  
  
        /// <summary>  
        /// Writes property values into a property bag.  
        /// </summary>  
        /// <param name="pb">Property bag.</param>  
        /// <param name="propName">Name of property.</param>  
        /// <param name="val">Value of property.</param>  
        private static void WritePropertyBag(Microsoft.BizTalk.Component.Interop.IPropertyBag pb, string propName, object val)  
        {  
            try  
            {  
                pb.Write(propName, ref val);  
            }  
            catch(Exception ex)  
            {  
                throw new ApplicationException( ex.Message);  
            }  
        }  
    }  
```