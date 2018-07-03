---
title: 步驟 17： 建立 WSClient 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WSClient application
- message enrichment tutorial, WSClient application
- creating, WSClient application
ms.assetid: 2849cd4c-30d0-47ab-8161-fab379d5a548
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9da92bf7631b254ac8464cad058a6500305f01bf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993255"
---
# <a name="step-17-create-the-wsclient-application"></a>步驟 17： 建立 WSClient 應用程式
WSClient.exe （Web 服務用戶端） 已撰寫的主控台應用程式[!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)]，說明如何將資料傳送至協調流程發佈為 Web 服務，在先前的步驟。 WSClient 應用程式會接受四個的輸入參數順序： 病患名字、 中間名可姓氏，與社會安全號碼，分別。 若要將病患資訊傳送至您的 Web 服務中，使用下列命令列語法：  
  
```  
wsclient john henry smith 123456789  
```  
  
### <a name="to-create-the-wsclient-application"></a>若要建立 WSClient 應用程式  
  
1. 在 [方案總管] 中，以滑鼠右鍵按一下**解決方案 'BTAHL7V22Common'**，按一下**新增**，然後按一下**新專案**。  
  
2. 在**加入新的專案**對話方塊中，於**專案類型**窗格中，按一下 [ **Visual C#** 然後在**範本**] 窗格中，按一下**主控台應用程式**。  
  
3. 在 **名稱**欄位中，輸入**WSClient**。 在 **位置**欄位中，瀏覽至 **\<*磁碟機*\>: \Tutorial**，然後按一下 **確定**。 方案總管 樹狀結構中，新增 WSClient 和 Program.cs 檔案中會出現。  
  
4. 在 [方案總管] 中，以滑鼠右鍵按一下**WSClient**，然後按一下**加入 Web 參考**。  
  
5. 在 [加入 Web 參考] 對話方塊中，按一下**本機電腦上的 Web 服務**。 在本機電腦可用的 Web 服務，搜尋，並接著它們會以清單顯示。  
  
6. 在本機電腦上的 Web 服務清單中，按一下**BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort**，按一下**Operation_1**，然後按一下 **加入參考**.  
  
7. 按兩下 [Program.cs]。  
  
8. 下列程式碼複製並貼到 [Program.cs] 視窗：  
  
   ```  
   using System;  
  
   namespace WSClient  
   {  
      class Class1  
      {  
         [STAThread]  
         static void Main(string[] args)  
         {  
            try   
            {  
               localhost.DoorbellRoot req=new WSClient.localhost.DoorbellRoot();  
               req.FirstName=args[0];  
               req.MiddleName=args[1];  
               req.LastName=args[2];  
               req.SSN=args[3];  
               localhost.BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort sp=new WSClient.localhost.BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort();  
               sp.Operation_1(req);  
            }  
            catch (Exception ex)  
            {  
               Console.WriteLine(ex.Message);  
            }  
         }  
      }  
   }  
   ```  
  
9. 在 [方案總管] 中，以滑鼠右鍵按一下**WSClient**，然後按一下**建置**。 請確定在 [輸出] 視窗中出現的成功訊息。 如果沒有成功的訊息出現時，進行疑難排解**WSClient**。 [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] 將一份可執行檔，WSClient.exe，放入\<*磁碟機*\>: \Tutorial\WSClient\bin\Debug 資料夾。  
  
   請繼續進行[步驟 18： 測試您的新訊息擴充方案](../../adapters-and-accelerators/accelerator-hl7/step-18-test-your-new-message-enrichment-solution.md)。  
  
## <a name="see-also"></a>另請參閱  
 [訊息擴充教學課程](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)