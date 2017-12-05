---
title: "步驟 4： 建立 HeaderHelper 專案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects, helper projects
- private process tutorial, creating helper projects
ms.assetid: 82413537-032a-4368-8d77-d024a7c83b0b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2525e0e87106e2eeb82fb05b52b3ec69d4be876d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-4-creating-the-headerhelper-project"></a>步驟 4： 建立 HeaderHelper 專案
在此步驟中，您將建立 [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] 類別庫。 當私用程序協調流程接收到內送訊息時，HeaderHelper 類別庫會判斷是否需要轉換文件，並在需要轉換時，執行轉換。 這讓您的協調流程能夠搭配使用不同版本的 RosettaNet 實作架構 (RNIF) 文件。 此外，在傳送 3A2 回應訊息時，HeaderHelper 類別庫會在傳送訊息前執行其他的文件轉換。  
  
### <a name="to-create-the-headerhelper-project"></a>若要建立 HeaderHelper 專案  
  
1.  在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，請在 [方案總管] 中，以滑鼠右鍵按一下 Contoso 方案，指向**新增**，然後按一下 **新專案**。  
  
2.  在 [加入新的專案] 對話方塊的 [專案類型] 窗格中選取**Visual C#**。  
  
3.  在 [範本] 窗格中，選取**類別庫**範本。  
  
4.  在**名稱**方塊中，輸入**HeaderHelper**，然後按一下 **確定**建立專案。  
  
5.  在 方案總管 中，以滑鼠右鍵按一下**Class1.cs**檔案**HeaderHelper**專案中，按一下 **重新命名**，型別**HeaderHelper.cs**，然後按下**Enter**。  
  
### <a name="to-create-the-helper-class"></a>建立 Helper 類別  
  
1.  在 [方案總管] 中，展開**HeaderHelper**專案，然後再連按兩下**HeaderHelper.cs**節點以開啟 HeaderHelper 原始程式檔。  
  
2.  在原始程式檔中輸入下列程式碼，覆寫所有的現有程式碼：  
  
    ```  
    using System;  
    using System.Xml;  
  
    namespace ContosoPriceAndAvailability  
    {  
        public class Helper  
        {  
            static public XmlDocument NormalizeHeader( XmlDocument curPip )  
            {  
                string strInput = curPip.OuterXml;  
                try  
                {  
                    XmlDocument xDoc = new XmlDocument();  
  
                    strInput = strInput.Replace("<!DOCTYPE Pip3A2PriceAndAvailabilityQuery SYSTEM \"3A2PriceAndAvailabilityQueryMessageGuideline_v1_3.dtd\"[]>",String.Empty);  
                    strInput = strInput.Replace("<Pip3A2PriceAndAvailabilityQuery>","<Pip3A2PriceAndAvailabilityQuery xmlns=\"http://schemas.microsoft.com/biztalk/btarn/2004/3A2PriceAndAvailabilityQueryMessageGuideline_v1_3.dtd\">");  
                    strInput = strInput.Replace("xml:",String.Empty);  
                    strInput = strInput.Replace("b:",String.Empty);  
                    strInput = strInput.Replace("lang:",String.Empty);  
                    strInput = strInput.Replace("ns1:",String.Empty);  
  
                    xDoc.LoadXml(strInput);  
  
                    return xDoc;  
                }  
                catch(Exception ex)  
                {  
                    System.Diagnostics.Debug.Write( ex.Message );  
                    throw ex;  
                }  
            }  
  
            static public string ReturnSCWithDocType( XmlDocument xmlDoc )  
            {  
                try  
                {  
                    string sResponse = xmlDoc.InnerXml;  
                    sResponse=sResponse.Replace("ns0:",String.Empty);  
                    xmlDoc.LoadXml(sResponse);  
                    xmlDoc.DocumentElement.RemoveAllAttributes();  
                    sResponse = xmlDoc.InnerXml;  
  
                    sResponse = sResponse.Insert(0,"<!DOCTYPE Pip3A2PriceAndAvailabilityResponse SYSTEM \"3A2PriceAndAvailabilityResponseMessageGuideline_v1_3.dtd\">");  
                    sResponse = sResponse.Replace("ns0:",String.Empty);  
                    sResponse = sResponse.Replace("b:",String.Empty);  
                    sResponse = sResponse.Replace("lang:",String.Empty);  
                    sResponse = sResponse.Replace("ns1:",String.Empty);  
  
                    return sResponse;  
                }  
                catch(Exception ex)  
                {  
                    throw ex;  
                }  
            }  
        }  
    }  
    ```  
  
3.  按一下 [ **檔案** ] 功能表上的 [ **全部儲存**]。  
  
### <a name="to-create-a-strong-named-assembly-for-the-headerhelper-project"></a>為 HeaderHelper 專案建立強式名稱組件  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下**HeaderHelper**專案，然後再按一下**屬性**。  
  
2.  在 [HeaderHelper 屬性頁] 對話方塊中，選取**簽署**從 HeaderHelp 屬性窗格的左窗格中。  
  
3.  在右窗格中，按一下 **簽署組件**。  
  
4.  按一下**選擇強式名稱金鑰檔**文字方塊中，然後選取**\<瀏覽\>**從下拉式清單。  
  
5.  在 [選取檔案] 對話方塊中，移至 Contoso 組件的位置，然後按兩下**FabConPriceAvail.snk**。  
  
6.  按一下 [ **檔案** ] 功能表上的 [ **全部儲存**]。  
  
7.  在 [方案總管] 中，展開**HeaderHelper**專案中，展開 [**屬性**] 節點，然後再按兩下**AssemblyInfo.cs**節點以開啟 AssemblyInfo.cs原始程式檔。  
  
8.  在 AssemblyInfo.cs 原始程式檔中，於 AssemblyCulture 屬性的下一行輸入下列程式碼：  
  
    ```  
    [assembly: AssemblyKeyFile("../../../FabConPriceAvail.snk")]  
    ```  
  
9. 按一下 [ **檔案** ] 功能表上的 [ **全部儲存**]。  
  
### <a name="to-build-and-deploy-the-headerhelper-project"></a>建置與部署 HeaderHelper 專案  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下**HeaderHelper**專案，然後再按一下**建置**。  
  
2.  啟動**Visual Studio 2012 的命令提示字元**。  
  
3.  在命令提示字元中，移至的位置**HeaderHelper**專案輸出目錄 （\Bin\Debug 資料夾）。  
  
4.  在命令提示字元中，輸入**gacutil /if HeaderHelper.dll**按**Enter**安裝**HeaderHelper**組件**全域組件快取**.  
  
## <a name="see-also"></a>請參閱  
 [步驟 5：修改 Contoso 私用程序協調流程](../../adapters-and-accelerators/accelerator-rosettanet/step-5-modifying-the-contoso-private-process-orchestration.md)