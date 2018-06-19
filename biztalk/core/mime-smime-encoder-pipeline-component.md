---
title: MIME SMIME 編碼器管線元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipeline components, MIME/SMIME Encoder
- MIME/SMIME Encoder [pipeline component]
- BTS.EncryptionCert property
ms.assetid: 397505e6-47d0-4b63-9197-814ee4388369
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d6c6a79052d3294420c46bff2a1ce3c0ed869e48
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22263062"
---
# <a name="mime-smime-encoder-pipeline-component"></a><span data-ttu-id="1337a-102">MIME SMIME 編碼器管線元件</span><span class="sxs-lookup"><span data-stu-id="1337a-102">MIME-SMIME Encoder Pipeline Component</span></span>
<span data-ttu-id="1337a-103">MIME/SMIME 編碼器元件可以放置在傳送管線的編碼階段中。</span><span class="sxs-lookup"><span data-stu-id="1337a-103">The MIME/SMIME Encoder component can be placed into the Encode stage of a send pipeline.</span></span> <span data-ttu-id="1337a-104">它支援 7 位元、8 位元、二進位、quoted-printable、base64 以及 UUencode 編碼。</span><span class="sxs-lookup"><span data-stu-id="1337a-104">It supports 7bit, 8bit, binary, quoted-printable, base64, and UUencode encoding.</span></span> <span data-ttu-id="1337a-105">當地語系化資料字元集變更不會影響編碼。</span><span class="sxs-lookup"><span data-stu-id="1337a-105">Localized data character set changes do not affect the encoding.</span></span>  
  
 <span data-ttu-id="1337a-106">此元件可用以進行 MIME 編碼，使用加密與簽章憑證以簽署或加密外寄訊息。</span><span class="sxs-lookup"><span data-stu-id="1337a-106">This component can be used to either MIME encode, sign or encrypt an outgoing message with encryption and signing certificates.</span></span>  
  
 <span data-ttu-id="1337a-107">若傳送管線中具有設定為簽署訊息的編碼元件，而包含執行管線之主控件的 BizTalk 群組未設定使用簽章憑證，則外寄訊息將被擱置 (發出錯誤訊息) 到執行管線之主控件的擱置佇列中。</span><span class="sxs-lookup"><span data-stu-id="1337a-107">If there is an encoding component in the send pipeline that is configured to sign messages, and the BizTalk group that includes the host running the pipeline is not configured with a signing certificate, the outgoing message will be suspended (with the appropriate error) to the suspended queue of the host that is running the pipeline.</span></span> <span data-ttu-id="1337a-108">若在執行服務下的目前使用者之個人憑證存放區中找不到簽章憑證，則訊息將擱置到執行管線之主控件的擱置佇列中。</span><span class="sxs-lookup"><span data-stu-id="1337a-108">If the signing certificate cannot be found in the personal certificate store of the current user under which the service is running, the message will be suspended to the suspended queue of the host that is running the pipeline.</span></span>  
  
 <span data-ttu-id="1337a-109">若輸出管線中的編碼元件設定為加密輸出訊息，而在憑證存放區中找不到憑證，則訊息將擱置到執行管線之主控件的擱置佇列中。</span><span class="sxs-lookup"><span data-stu-id="1337a-109">If there is an encoding component in the outbound pipeline configured to encrypt outbound messages, and the certificate cannot be found in the certificate store, the message will be suspended to the suspended queue of the host that is running the pipeline.</span></span>  
  
 <span data-ttu-id="1337a-110">若要在接收已簽章和已加密訊息的要求-回應連接埠上執行回應加密，則自訂管線元件必須在 MIME/SMIME 編碼器管線元件之前加入管線。</span><span class="sxs-lookup"><span data-stu-id="1337a-110">To perform response encryption on a request-response port that is receiving signed and encrypted messages, a custom pipeline component must be added to the pipeline before the MIME/SMIME Encoder pipeline component.</span></span> <span data-ttu-id="1337a-111">此自訂管線元件必須識別對應至加密憑證的指紋，並且將它設定為**BTS。EncryptionCert**在訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="1337a-111">This custom pipeline component must identify the thumbprint corresponding to the encryption certificate and set it to the **BTS.EncryptionCert** property on the message context.</span></span> <span data-ttu-id="1337a-112">如需訊息內容屬性的詳細資訊，請參閱[如何修改群組內容](../core/how-to-modify-group-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="1337a-112">For more information about message context properties, see [How to Modify Group Properties](../core/how-to-modify-group-properties.md).</span></span>  
  
 <span data-ttu-id="1337a-113">如需設定 MIME/SMIME 編碼器管線元件的資訊，請參閱[如何設定 MIME SMIME 編碼器管線元件](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md)。</span><span class="sxs-lookup"><span data-stu-id="1337a-113">For information about configuring the MIME/SMIME Encoder pipeline component, see [How to Configure the MIME-SMIME Encoder Pipeline Component](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md).</span></span> <span data-ttu-id="1337a-114">如需 BizTalk Server 支援加密、 簽署及憑證的使用方式的詳細資訊，請參閱[傳送和接收訊息的安全性](../core/security-for-sending-and-receiving-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="1337a-114">For more information about BizTalk Server support for encryption, signing, and usage of certificates, see [Security for Sending and Receiving Messages](../core/security-for-sending-and-receiving-messages.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1337a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1337a-115">See Also</span></span>  
 <span data-ttu-id="1337a-116">[管線元件](../core/pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="1337a-116">[Pipeline Components](../core/pipeline-components.md) </span></span>  
 <span data-ttu-id="1337a-117">[MIME SMIME 屬性結構描述和屬性](../core/mime-smime-property-schema-and-properties.md) </span><span class="sxs-lookup"><span data-stu-id="1337a-117">[MIME-SMIME Property Schema and Properties](../core/mime-smime-property-schema-and-properties.md) </span></span>  
 [<span data-ttu-id="1337a-118">MIME （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="1337a-118">MIME (BizTalk Server Sample)</span></span>](../core/mime-biztalk-server-sample.md)