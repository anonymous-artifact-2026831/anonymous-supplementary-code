# Official data acquisition and redistribution boundary

RefAmb draws its 1,500 selected examples from the four sources below. Obtain
the actual questions, answers, images, and retrieval resources from these
official releases; then use `refamb_1500_manifest.jsonl` to identify the exact
records included in RefAmb. The links are provenance pointers, not a
sublicence or redistribution of their data.

| RefAmb source | Official release | How the manifest identifies its records |
|---|---|---|
| CRAG-MM | https://github.com/facebookresearch/CRAG-MM | `source_dataset`, `source_split=single_turn`, and `source_record_id`; preserve the stated CC BY-NC 4.0 attribution/non-commercial restrictions. |
| InfoSeek | https://github.com/open-vision-language/infoseek | `source_split=val_unseen_entity`, `source_record_id`, and `source_image_id`; obtain images/annotations only from the official release. |
| MC-Search | https://huggingface.co/datasets/YennNing/MC-Search | `source_record_id` and `source_image_id`; follow the dataset-card terms and obtain its knowledge base/images from the official repository. |
| OVEN | https://github.com/open-vision-language/oven | `source_split`, `source_record_id`, and `source_image_id` when present; use OVEN's official image-download procedure. |

We do not redistribute upstream question text, answer text, images, document
collections, or image-download artifacts. Before publishing any augmented
RefAmb release, verify every component license; in particular, web-derived and
OVEN-referenced images may have rights separate from benchmark annotations.
