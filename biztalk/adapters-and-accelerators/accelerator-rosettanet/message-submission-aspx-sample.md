---
title: "訊息提交 ASPX 範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8358f849-231f-432c-9fc2-6efdcf95580d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12fb7d90485014a62ed9010590d27a79ecd925c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-submission-aspx-sample"></a>訊息提交 ASPX 範例
本主題提供範例 .aspx 程式碼，讓您可以用來提交服務內容至私用程序。 您可以使用這個 .aspx 程式碼來代替商務營運系統 (LOB) 應用程式。  
  
## <a name="demonstrates"></a>示範  
 這段程式碼會示範如何呼叫 `SubmitRNIF` 方法來提交訊息，其中包含下列步驟：  
  
-   設定由應用程式輸入的訊息參數  
  
-   設定訊息類別  
  
-   如果提交的值為空值或空白，則產生該訊息的「交易夥伴介面程序 (PIP)」執行個體。  
  
-   產生輸入附件檔案陣列和註解  
  
## <a name="example"></a>範例  
 這段程式碼會接受來自前端應用程式 (例如瀏覽器、[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]® 或 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® Word) 的輸入，並產生啟動者私用程序可以使用的 XML 文件。  
  
 LOBWebApplication 公用程式包含下列程式碼。 如需詳細資訊，請參閱[LOBWebApplication](../../adapters-and-accelerators/accelerator-rosettanet/lobwebapplication.md)。  
  
```  
using System;  
using System.IO;  
using System.Text;  
using System.Data;  
using System.Drawing;  
using System.Collections;  
using System.ComponentModel;  
using System.Web;  
using System.Web.UI;  
using System.Web.SessionState;  
using System.Web.UI.WebControls;  
using System.Web.UI.HtmlControls;  
using Microsoft.Solutions.BTARN.SubmitRNIF;  
  
namespace Microsoft.Solutions.BTARN.SDK  
{  
      /// <summary>  
      /// Calls SubmitRNIF to submit service content to the BTARN private process.  
      /// </summary>  
      public class AspxLobApplication : System.Web.UI.Page  
      {  
            private void Page_Load(object sender, System.EventArgs e)  
            {  
                  Request.ValidateInput();  
  
                  string sPipCode=Request["PipCode"];  
                  string sPipVersion=Request["PipVersion"];  
                  string sPipInstanceID=Request["PipInstanceID"];  
                  string sPipCategory=Request["PipCategory"];  
                  string sPipSource=Request["PipSource"];  
                  string sPipDestination=Request["PipDestination"];  
                  string sFileName1=Request["FileName1"];  
                  string sFileName2=Request["FileName2"];  
                  string sRemark1=Request["Remark1"];  
                  string sRemark2=Request["Remark2"];  
                  string[] aInputFiles = new string[2];  
                  string[] aRemarks = new string[2];  
                  string sContent = Request["Textarea1"];  
  
                  SubmitRNIF.SubmitRNIF MessageSubmitter = new SubmitRNIF.SubmitRNIF();  
  
                  //The message category  
                  SubmitRNIF.SubmitRNIF.MessageCategory mc;  
                  if(sPipCategory.ToUpper() == "RESPONSE")   
                        mc=SubmitRNIF.SubmitRNIF.MessageCategory.Response;  
                  else  
                        mc=SubmitRNIF.SubmitRNIF.MessageCategory.Action;  
  
                  //Generate a PIP instance ID if the submitted value is null or empty  
                  if(sPipInstanceID.Length==0)  
                        sPipInstanceID=Guid.NewGuid().ToString();  
  
                  //Generate the input attachment files array and its associated remarks  
                  if(sFileName1!=null && sFileName1.Length>0) aInputFiles[0]=sFileName1;  
                  if(sFileName2!=null && sFileName2.Length>0) aInputFiles[1]=sFileName1;  
                  if(sRemark1!=null && sRemark1.Length>0) aRemarks[0]=sRemark1;  
                  if(sRemark2!=null && sRemark2.Length>0) aRemarks[1]=sRemark2;  
  
                  if(sFileName1==null && sFileName2==null)  
                        MessageSubmitter.SubmitMessage(mc, sPipSource, sPipDestination, sPipCode, sPipInstanceID, sPipVersion, sContent);  
                  else  
                        MessageSubmitter.SubmitMessage(mc, sPipSource, sPipDestination, sPipCode, sPipInstanceID, sPipVersion, sContent, aInputFiles);  
            }  
  
            #region Web Form Designer generated code  
...  
      }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [LOBWebApplication](../../adapters-and-accelerators/accelerator-rosettanet/lobwebapplication.md)   
 [傳訊範例](../../adapters-and-accelerators/accelerator-rosettanet/messaging-samples.md)