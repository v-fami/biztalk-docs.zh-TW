---
title: "SFT HL7 訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5bf3ac5-8197-4ea3-ace8-ff59ac32313c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58cf1536d8619e47a9a33c77e4f95387e0ebb559
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sft-in-hl7-messages"></a><span data-ttu-id="dbc4b-102">SFT HL7 訊息中</span><span class="sxs-lookup"><span data-stu-id="dbc4b-102">SFT in HL7 Messages</span></span>
[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]<span data-ttu-id="dbc4b-103">加入訊息中的軟體區段 (SFT) 的支援。</span><span class="sxs-lookup"><span data-stu-id="dbc4b-103"> supports adding software segments (SFT) to messages.</span></span> <span data-ttu-id="dbc4b-104">SFT 區段提供做為傳送應用程式的軟體產品相關的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="dbc4b-104">SFT segments provide additional information about the software products used as sending applications.</span></span> <span data-ttu-id="dbc4b-105">SFT 區段主要用於診斷。</span><span class="sxs-lookup"><span data-stu-id="dbc4b-105">SFT segments are primarily used for diagnostics.</span></span> <span data-ttu-id="dbc4b-106">標準 HL7 2.5 版的一部分 SFT 區段會顯示在應用程式通知。</span><span class="sxs-lookup"><span data-stu-id="dbc4b-106">As a part of the HL7 v2.5 standard, SFT segments are displayed in the application acknowledgement.</span></span>  
  
## <a name="message-instance-with-sft-segment"></a><span data-ttu-id="dbc4b-107">SFT 區段的訊息執行個體</span><span class="sxs-lookup"><span data-stu-id="dbc4b-107">Message instance with SFT segment</span></span>  
 <span data-ttu-id="dbc4b-108">使用下列程序來建立以 SFT 區段 ADT^A01.txt 訊息。</span><span class="sxs-lookup"><span data-stu-id="dbc4b-108">Use the following procedure to create an ADT^A01.txt message with an SFT segment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dbc4b-109">當您建立此訊息在 [記事本] 中時，刪除傳回的最後一個的那一行的歸位字元。</span><span class="sxs-lookup"><span data-stu-id="dbc4b-109">When you create this message in Notepad, delete the carriage return following the last line.</span></span>  
  
#### <a name="to-create-an-adta01txt-message-with-an-sft-segment"></a><span data-ttu-id="dbc4b-110">若要建立 ADT^A01.txt 訊息以 SFT 區段</span><span class="sxs-lookup"><span data-stu-id="dbc4b-110">To create an ADT^A01.txt message with an SFT segment</span></span>  
  
1.  <span data-ttu-id="dbc4b-111">開啟 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="dbc4b-111">Open Notepad.</span></span>  
  
2.  <span data-ttu-id="dbc4b-112">將下列文字複製到 [記事本]:</span><span class="sxs-lookup"><span data-stu-id="dbc4b-112">Copy the following text into Notepad:</span></span>  
  
    ```  
    MSH|^~\&|Tutorial_ADTSystem|MCM|Tutorial_BatchDest||199112311501||  
    ADT^A01|000001|P|2.5|||AL|AL  
    SFT|ST^A^1^2^ISO^String&String&DNS^AM^String&String&DNS^P^String|  
    String|String|String|String|DTM^H  
    EVN|P12|DTM^D|DTM^H|01|ST^ST&ST&ST&ST&ST|DTM^H|Table^ST^DNS  
    PID||ST^ST^ISO|ST^ST^ISO|ST^ST^ISO|surname^prefix^own^spouse^partner  
    |surname^prefix^own^spouse^partner|DTM^H|A|  
    surname^prefix^own^spouse^partner|ST^ST^ACR^ST^ST^ACR|  
    address^street^number|countrycode|ST^ASN^BP|ST^ASN^BP|  
    ST^ST^ACR^ST^ST^ACR|||ST^ST^ISO|ST|ST^Table^DT|ST^ST^ISO||  
    ST|N|1|ST^ST^ACR^ST^ST^ACR|||DTM^H|N|N|US|DTM^H|Table^String^DNS|  
    ST^ST^ACR^ST^ST^ACR|ST^ST^ACR^ST^ST^ACR|String|  
    ST^ST^ACR^ST^ST^ACR  
    PD1|C|A|||F|string|F|F|N||ST^ST^ACR^ST^ST^ACR|N|string||  
    ST^ST^ACR^ST^ST^ACR|A|string|string|USA|E1... E9|ACT  
    ROL||AD|ST^ST^ACR^ST^ST^ACR|ST^surname&prefix&own&partner&spouse|  
    DTM^H|DTM^H|ST^ST^ACR^ST^ST^ACR|ST^ST^ACR^ST^ST^ACR|ST^ST^ACR  
    ^ST^ST^ACR|ST^ST^ACR^ST^ST^ACR  
    PV1||B||A|ST^ST^ISO|||||CAR||ST|R|9|A9|ST||ST|ST^ST^ISO|ST^DTM&H|  
    ST|ST|ST|ST|ST|1|1|ST|ST|ST|ST|3|3|ST|ST|06||ST^ST^ACR^ST^ST^ACR|  
    ST|H|ST|||DTM^H|DTM^H||||||A  
    PV2||ST^ST^ACR^ST^ST^ACR|ST^ST^ACR^ST^ST^ACR|ST^ST^ACR^ST^ST^ACR|  
    String|String|HO|DTM^H|DTM^H|1|1|string||string|N|D|string|CH|N|  
    1|F|N||AI|1|sttring|01|strhi|edwqed|ST^ST^ACR^ST^ST^ACR|jhgjk|N|  
    DTM^H|N|N|N|N|ST^ST^ACR^ST^ST^ACR|ST^ST^ACR^ST^ST^ACR|  
    ST^ST^ACR^ST^ST^ACR|ST^ST^ACR^ST^ST^ACR|ST^ST^ACR^ST^ST^ACR|F|F|  
    ST^ST^ACR^ST^ST^ACR|jhklh|DTM^H|DTM^H|L  
    ROL||AD|ST^ST^ACR^ST^ST^ACR|ST^surname&prefix&own&partner&spouse|  
    DTM^H|DTM^H|ST^ST^ACR^ST^ST^ACR|ST^ST^ACR^ST^ST^ACR|  
    ST^ST^ACR^ST^ST^ACR|ST^ST^ACR^ST^ST^ACR  
    DB1|1|AP|ST^ST|N|string|string|string|string  
    OBX|1|AD|ST^ST^ACR^ST^ST^ACR|string|string|ST^ST^ACR^ST^ST^ACR|  
    string|AA|1|A|C|DTM^H|string|DTM^H|ST^ST^ACR^ST^ST^ACR||  
    ST^ST^ACR^ST^ST^ACR  
    AL1|1|ST^ST^ACR^ST^ST^ACR|ST^ST^ACR^ST^ST^ACR||string|string  
    DG1|1|ST|ST^ST^ACR^ST^ST^ACR|ST|DTM^H|A|ST^ST^ACR^ST^ST^ACR|  
    ST^ST^ACR^ST^ST^ACR|N|ST|ST^ST^ACR^ST^ST^ACR||||1||R|N|DTM^H||A  
    DRG|ST^ST^ACR^ST^ST^ACR|DTM^H|N|ST|ST^ST^ACR^ST^ST^ACR|||C||N|E  
    PR1|1|ST|ST^ST^ACR^ST^ST^ACR|ST|DTM^H|A|||ST|1|||  
    ST^ST^ACR^ST^ST^ACR|0|ST^ST^ACR^ST^ST^ACR|ST^ST^ACR^ST^ST^ACR|1|  
    ST^ST^ACR^ST^ST^ACR||A  
    ROL||AD|ST^ST^ACR^ST^ST^ACR|ST^surname&prefix&own&partner&spouse|  
    DTM^H|DTM^H|ST^ST^ACR^ST^ST^ACR|ST^ST^ACR^ST^ST^ACR|  
    ST^ST^ACR^ST^ST^ACR|ST^ST^ACR^ST^ST^ACR  
    IN1|1|ST^ST^ACR^ST^ST^ACR|ST|||surname&prfix&own&partner&spouse|  
    ST^ASN^BP^ST^1^1^1^1^ST^ST^ST^ST|string||||string|string|  
    ST^DT^ST|string|surname&prefix&own&partner&spouse|  
    ST^ST^ACR^ST^ST^ACR|DTM^H||M|CO|string|N|string|N|string|_|  
    string|DTM^H||M|string|1|1|string  
    IN2||string||string|E|string|surname&prefix&own&partner&spouse|  
    string|surname&prefix&own&partner&spouse|string  
    IN3|1|||N||DTM^H|DTM^H||string|string  
    ROL||AD|ST^ST^ACR^ST^ST^ACR|ST^surname&prefix&own&partner&spouse|  
    DTM^H|DTM^H|ST^ST^ACR^ST^ST^ACR|ST^ST^ACR^ST^ST^ACR|  
    ST^ST^ACR^ST^ST^ACR|ST^ST^ACR^ST^ST^ACR  
    ACC|DTM^H|ST^ST^ACR^ST^ST^ACR|string|ST^ST^ACR^ST^ST^ACR|N|N||  
    string|string|N  
    UB1|1|1|1|1|1|1|string|1|1||1|ST^ST^ACR^ST^ST^ACR|  
    ST^ST^ACR^ST^ST^ACR|string|string||ST^ST^ACR^ST^ST^ACR|string|  
    string|string|string|string|string  
    UB2|1|string|string|string|string||||string|string|string|string|  
    string|string|string|string|1  
    PDA|ST^ST^ACR^ST^ST^ACR||N|DTM^H|  
    ST^surnamr&prefix&own&partner&spouse|N||  
    ST^surnamr&prefix&own&partner&spouse|N  
    ```  
  
3.  <span data-ttu-id="dbc4b-113">儲存檔案，然後關閉記事本。</span><span class="sxs-lookup"><span data-stu-id="dbc4b-113">Save the file, and then close Notepad.</span></span>  
  
4.  <span data-ttu-id="dbc4b-114">請檢查來源合作對象的 [通知] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="dbc4b-114">Check the Acknowledgement folder of the source party.</span></span>  
  
     <span data-ttu-id="dbc4b-115">此訊息的本文通知會包含訊息的 SFT 區段。</span><span class="sxs-lookup"><span data-stu-id="dbc4b-115">The body acknowledgement of this message contains the SFT segments of the message.</span></span> <span data-ttu-id="dbc4b-116">會出現上述訊息的通知：</span><span class="sxs-lookup"><span data-stu-id="dbc4b-116">The ACK for the above message is:</span></span>  
  
    ```  
    MSH|^~\&|Tutorial_BatchDest||Tutorial_ADTSystem|MCM|20070508175311||ACK^A01^ACK|000001|P|2.5|||AL  
    MSA|AA|000001  
    SFT|ST^A^1^2^ISO^String&String&DNS^AM^String&String&DNS^P^String|String|String|String|String|DTM^H  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="dbc4b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbc4b-117">See Also</span></span>  
 <span data-ttu-id="dbc4b-118">[HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/hl7-messaging.md) </span><span class="sxs-lookup"><span data-stu-id="dbc4b-118">[HL7 Messaging](../../adapters-and-accelerators/accelerator-hl7/hl7-messaging.md) </span></span>  
[<span data-ttu-id="dbc4b-119">了解 HL7 加速器以及可用的 BizTalk 工具</span><span class="sxs-lookup"><span data-stu-id="dbc4b-119">Learn the HL7 accelerator and the BizTalk tools available</span></span>](../../adapters-and-accelerators/accelerator-hl7/learn-the-hl7-accelerator-and-the-biztalk-tools-available.md)